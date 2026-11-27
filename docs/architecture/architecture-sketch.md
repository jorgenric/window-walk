# Architecture sketch

A small TypeScript stack: one Node API and admin app on Render, Postgres with full-text, vector and geographic search, object storage for photos, and a mostly static public site rebuilt from the database. It fits a volunteer budget and a Phase 1 pilot, and grows into the later phases without a rewrite.

## Components

Choices are the defaults from [decision 0006](../decisions/0006-stack-and-license.md).

| Component | Role | Choice |
| --- | --- | --- |
| Public site | Shop pages, region pages, walk-a-street, themes, Hometown Shelf feeds | Astro static pages, CDN-cached, rebuilt when data changes |
| Storefront builder | Owner interview, photo upload, claim flow | Same Astro app: server-rendered routes (Node adapter) with small interactive components; phone-first, autosave |
| Admin console | Moderation, eligibility, report queue, curation, exposure dashboard, admin log browser | Same Astro app, role-gated |
| API | Shops, products, reports, votes, follows, feeds, admin actions | Fastify + TypeScript on Render |
| Database | Structured shop and product data, regions, search | Postgres with full-text search, pgvector, PostGIS and `ltree`, on Render |
| Photo storage | Storefront, interior, owner, Hometown Shelf images | Cloudflare R2 (S3-compatible), resized on upload |
| Background jobs | Image tagging, embeddings, nudges, digests, OSM import, feed builds, log exports | A worker on Render plus a scheduled job runner |
| Email | Claim codes, vote confirmations, owner nudges, follower updates, digests | Postmark, behind a small interface so it can be swapped |

## Core data model

| Entity | Key fields | Notes |
| --- | --- | --- |
| Shop | name, slug, presence type, address or neighborhood, geo point, hours, phone, links, story fields, status, last confirmed date | Presence type: storefront, market, studio, online-first |
| Region | name, slug, level, kind (place or community area), parent, path, boundary geometry, stewards, status | Places form a strict tree; community areas can overlap it |
| Region membership | shop, region, is primary | Computed from shop location and region boundaries; recomputed when either changes |
| Corridor order | region, ordered list of shops | Only for corridor regions; drives walk-a-street order |
| User | email, verified flag | Login by email magic link; no passwords; one account can be both owner and admin |
| Owner claim | user, shop, role (primary or editor), method, verified by, date, status | Edit rights for a shop; one primary, up to five editors |
| Admin role | user, region, role type, granted by, dates | Covers the region and everything below it |
| Affiliation | user, shop or organization, relationship, declared date | Drives conflict checks; visible to all admins |
| Competitor link | shop, shop, source (computed or flagged) | Category-and-distance matches plus manual flags |
| Admin action | sequence number, actor, role, region, action type, target, before, after, reason, timestamp, previous entry hash | Append-only, tamper-evident |
| Photo | shop, kind (storefront, interior, owner), date added, tags | Tags from image model, reviewed by owner |
| Shelf item | shop, photo, caption, price range, highlight tag, tag expiry, date added | The Hometown Shelf; "New" expires automatically |
| Carries | shop, category tags, known for, unexpected items, embedding | Powers "what we carry" search |
| Report | shop, type, note, reporter hash, status, routed to | Never public; escalation timestamps |
| Vote | shop, voter hash, period | Feeds the favorites pool; counts never shown |
| Exposure | shop, region, slot, date, impression count | Aggregated daily for fairness, per region |
| Follow | shop or region, email, confirmed flag | Double opt-in; used only for updates |
| Collection | title, curator, region, shops, start and end dates | Curated themes, scoped to a region |

## Key flows

1. **Seeding:** a job imports OSM shop tags for a corridor, cross-checks the Oregon registry, and creates unclaimed stub shops for volunteer review.
2. **Claiming:** an owner requests a claim, gets a code by mail, phone or association vouch, and gains edit rights.
3. **Publishing:** saving a page triggers jobs that resize photos, tag images, refresh embeddings, rebuild the page and feeds, and notify followers when the Hometown Shelf has new items.
4. **Discovery:** each region page request picks shops per slot by the rotation rules for that region, logging exposure against it.
5. **Search:** a query is embedded and matched against shop and shelf embeddings, blended with full-text scores and filtered to the chosen region and everything below it; results say "likely carries."
6. **Admin actions:** every admin write goes through one service that checks role scope and conflicts, applies the change and writes the log entry in the same transaction.
7. **Region registration:** a proposed region is checked for overlap and naming, approved by a parent-region admin, then shop memberships are computed and its pages go live.
8. **Freshness:** a scheduled job sends owner nudges, escalates stale reports to region stewards and admins, and expires "New" tags.

## Regions

- **Tree storage:** each region stores its parent and a materialized path, such as `or.portland.alberta-arts.alberta-st`, so "this region and everything below it" is one indexed query (Postgres `ltree`).
- **Boundary sources:** Portland neighborhoods from PortlandMaps `Public/Boundaries` layer 1 and city limits from layer 13, with OSM administrative boundaries elsewhere ([decision 0003](../decisions/0003-region-defaults.md)). Portland's shared-area polygons ("A/B") give a shop membership in both neighborhoods, with the first-named as primary. A working import is in [poc/parkrose-seed-data](../../poc/parkrose-seed-data/).
- **Activation:** a region gets its own page, slots and digest at five published shops; below that, the parent region's page shows its shops as a section.
- **Geometry:** region boundaries and shop points live in PostGIS. Membership is a point-in-polygon check, cached in the region membership table so page and search queries don't redo the geometry.
- **Roll-up:** a shop's primary region is the smallest place that contains it. Ancestor regions include it through the path, not through duplicate rows.
- **Routing:** URLs mirror the place path (`/or/portland/alberta-arts/alberta-st`). Community areas get their own path under the place that contains them, plus a short alias. Every listing, search, feed and API endpoint takes a region parameter.
- **Placement by presence type:** storefronts use their address point, studios and home-based sellers an approximate neighborhood point, market vendors their market's region plus dates, and online-first brands their home neighborhood.
- **Static builds:** each region page is generated like a shop page, and a shop change rebuilds its pages and its ancestor regions' feeds.

## Admin accountability

- **Single write path:** admin changes go only through an admin action service. Database permissions stop the app from touching moderated tables any other way.
- **Append-only log:** the app's database user can insert into the admin action table but not update or delete it, and a trigger rejects any attempt. Each entry stores a hash of the previous entry, so a missing or altered row breaks the chain.
- **Outside copies:** a scheduled job exports new log entries and the latest chain hash to storage controlled by the home organization, so a database admin couldn't quietly rewrite history.
- **Authorization check, in order:** (1) the role covers the target's region, (2) the actor isn't affiliated with the target shop, (3) the actor isn't affiliated with a competitor of the target, (4) drastic actions have a second approval from an unconflicted admin. Blocked actions are routed to eligible admins, and the block itself is logged.
- **Competitor computation:** a nightly job links shops with the same primary interest chip that are in the same neighborhood or within 1.6 km. Manual flags add to it and persist until an unconflicted moderator removes them. Admins can view the result ([decision 0004](../decisions/0004-administration-defaults.md)).
- **Second approvals:** drastic actions are stored as pending until a second unconflicted admin approves, and they expire after 7 days. Both the request and the approval are logged.
- **Role lifecycle:** roles carry a start and end date (one year), and a scheduled job lapses roles with no actions in six months.
- **Views:** a log browser for all admins, filterable by admin, shop, region, action and date; a per-shop history for owners; a periodic per-admin activity summary; and a public monthly summary per region with counts only.

## Claims

- **Verification methods:** postcard code (30-day expiry), phone or text code to the pre-recorded public number (15 minutes), email at the shop website's domain, association or market vouch, or a steward in person. Five attempts per claim ([decision 0002](../decisions/0002-independence-stub-pages-and-claims.md)).
- **Data:** an owner claim records its method and verifier. Each shop has one primary owner and up to five editors.
- **Disputes and transfers:** a competing claim locks the page to its current content and opens a two-admin review. A transfer waits 14 days for the previous owner to object.
- **Stub pages:** a shop's status (stub, claimed, hidden) controls what the page renders and keeps stubs out of featured slots.

## Tunable settings

Featuring, voting and freshness values from [decision 0005](../decisions/0005-featuring-and-freshness-parameters.md) live in a settings table, scoped to a region with inheritance from the parent region. Changing a region's featuring settings is a drastic action, so it goes through the admin action service.

## Search and image tagging

- Embeddings for each shop's carries text and each shelf item caption, stored in pgvector
- Image tagging of interior and shelf photos with a vision model; tags shown to owners for approval before they affect search
- Hybrid ranking: semantic similarity plus keyword match plus distance; no ranking by votes or payment

## Open formats and integrations

- schema.org LocalBusiness and Product markup on every page
- RSS per shop, per corridor and for Hometown Shelf highlights; iCal for market dates and events
- OSM contribution workflow for corrected hours (manual review first)
- Google Business Profile sync in Phase 3, owner-authorized

## Privacy and security

- No shopper accounts for browsing; interest chips and passport stored in the browser only
- Voter and reporter identities stored as salted hashes; owners never see who reported
- Home-based sellers store a neighborhood and an approximate point, never a street address
- Owner login by email magic link with rate limiting; admin roles separate from owner roles

## Phase 1 build scope

Shop, region (with the full place tree seeded for Oregon, Portland, the pilot neighborhood and corridor), user, claim, admin role, affiliation, admin action, photo, shelf item and report entities; region links and filters, builder, claim flow, shop pages, walk-a-street, wildcard and curated slots, report queue, the admin action service with conflict checks and the log browser, follow by email, schema.org markup, and the QR poster generator. Search, voting, digests, syncs and open region registration wait for Phases 2 and 3.
