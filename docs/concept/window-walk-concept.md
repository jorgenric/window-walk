# Window Walk: Concept

Draft as of Nov 26, 2026 · @Eric. Default values for open questions are recorded in [decisions 0002 to 0006](../decisions/).

## Purpose and principles

Window Walk is a community-run service that helps residents discover, connect with and keep supporting local businesses that sell goods, starting in one Portland neighborhood. It is a civic project, not a business: success means more local spending and stronger shop-customer relationships, not revenue for the service.

Guiding principles:

- **Discovery should be fun.** Browsing feels like window shopping and getting to know the neighborhood, not querying a database.
- **Character over catalog.** Photos, owner stories and what a shop is known for matter more than item-level stock, which small shops can't keep current.
- **Visit or call is the goal.** Every page points shoppers to the shop itself, wherever the shop does business.
- **Useful with few participants.** A single well-made storefront page is worth visiting, so the service has value before it has scale.
- **Fair visibility.** No money, votes, activity or admin favoritism can buy permanent placement. Randomness is always part of the mix.
- **No ads, no public ratings, no shopper tracking.** Browsing needs no account.
- **Owners own their content.** Pages are exportable, data is shared in open formats, and the relationship with customers belongs to the shop.
- **Accountable administration.** Every admin action is permanently logged where all admins can see it, and nobody acts on their own shop or a competitor's.
- **Regional by design.** Every view can be scoped to a street, neighborhood, city or state, and those levels nest.

## Who it serves

**Eligibility rule:** local businesses selling goods that compete with remote sellers and do not themselves have easy access to outside markets. In practice, any independent shop that sells home goods a household could otherwise buy from Amazon or another online mass retailer fits ([decision 0001](../decisions/0001-eligibility-online-substitutable-goods.md)).

| Group | Fit | Notes |
| --- | --- | --- |
| Independent retail (hardware, books, toys, gear, kitchen, used, vintage) | Core | Compete directly with online and national chains |
| Local makers and market vendors | Core | Often no storefront; listed with where and when to find them |
| Specialty food and packaged goods shops, including independent grocers and ethnic markets | Core | Goods you could otherwise order online |
| Home, appliance, flooring, auto and bike parts, electronics and variety stores | Core | Independent alternatives to ordering household goods online |
| Fresh-food shops (bakeries, butchers, delis), restricted goods, service-led shops (opticians, tire shops) | Case by case | In when a meaningful share of stock is online-substitutable |
| Hybrids (a bike shop with a service bench, a camera shop with repairs) | In | Qualify through the goods side |
| Online-first local brands that already ship nationally | Lower priority | Included mainly when they also sell through local shops or markets |
| Pure services (salons, contractors, consultants), restaurants, cafes | Out | Already inherently local and well served by Google Maps and Yelp |
| Chains and franchises, cannabis | Out | Not independent, or not sold online |

**Independent and local** means not a franchise or chain location, owners based in Oregon or SW Washington, and no more than five retail locations. Co-op members such as True Value stores, and local nonprofit shops, count. Owners attest when they claim, and a moderator checks the state business registry ([decision 0002](../decisions/0002-independence-stub-pages-and-claims.md)).

Physical storefronts are not required. Each page has a **"how to find us"** type:

- **Storefront:** address, hours, and a place in the walk-a-street view
- **Market or pop-up:** where and when they appear
- **Studio or home-based:** neighborhood only, never a home address, with "call or message to arrange"
- **Online-first:** website plus local pickup or the shops that stock them

Maker and shop pages cross-link ("find our goods at" and "local makers we carry"), building a visible web of local relationships.

## Regions and community views

The application is regional at its core. Every page, list, feed and featured slot belongs to a region, and regions nest from a single street up to a state. A pilot corridor is simply the first region with shops in it. Adding the next street, neighborhood or city is setup work, not a rebuild.

**Levels**

| Level | Example | Typical use |
| --- | --- | --- |
| State | Oregon | Statewide themes and seasonal collections; entry point to cities |
| City or town | Portland | City-wide browsing, search and digests |
| Neighborhood | Alberta Arts | The everyday "my area" view |
| Corridor or street | NE Alberta St, 15th to 33rd | Walk-a-street; ordered storefronts |

The levels are not fixed. Optional metro or county and district levels are available where a place needs them, and a small town may skip neighborhoods. A region gets its own page, featured slots and digest once it has five published shops; until then its shops show as a section of the parent region ([decision 0003](../decisions/0003-region-defaults.md)).

**Boundaries** come from official government layers wherever they're open. In Portland that's the city's neighborhood and city-limit layers on PortlandMaps. Shops in Portland's shared areas, such as Roseway/Madison South, belong to both neighborhoods. When a local name doesn't match the official map, it becomes a community area rather than a change to the places tree. Gateway, for example, is a business district spanning parts of three neighborhoods.

**Two kinds of region**

- **Places:** the main nested tree of state, city, neighborhood and corridor. Each place has one parent, so breadcrumbs and URLs are always clear.
- **Community areas:** extra regions that can overlap the tree, such as a business district crossing neighborhood lines or a market's vendor area. They show up as views and filters without breaking the main hierarchy.

**How it works for shoppers**

- **A link for every level.** Each region has a stable, readable address, such as `/or/portland/alberta-arts/alberta-st`. Any page can be shared at the level it shows.
- **Zoom in and out.** Breadcrumbs and a level switcher move from a street out to its neighborhood, city or state and back, keeping search terms, interest chips and themes.
- **Filter anything by region.** Search, theme pages, Hometown Shelf feeds, events and "surprise me" all take a region filter at any level.
- **Shops roll up.** A shop belongs to the smallest region that contains it and appears automatically in every region above it. An Alberta St shop shows up in Alberta Arts, Portland and Oregon.
- **Placement by "how to find us" type.** Storefronts are placed by address. Studios and home-based sellers are placed by neighborhood only. Market vendors appear wherever and whenever they set up. Online-first brands appear under their home neighborhood.
- **Fair at every level.** Featured slots, rotation and exposure tracking run separately for each region, so a busy downtown can't crowd out a quiet street in a city-wide view.
- **Follow at any level.** Shoppers can follow updates and digests for a street, a neighborhood or a whole city.

**Registering a community view**

Neighborhood groups, business associations, market organizers or city programs can register a region:

1. Propose a name, level, parent region and boundary. The boundary can be drawn, chosen from official neighborhood or city boundaries, or set as a list of street segments for a corridor.
2. Name one or more stewards to curate the view, run storefront days and handle local reports.
3. An admin of the parent region reviews the request against overlap and naming rules. The approval goes into the admin action log. A new city or town also needs a local host organization, or two stewards with no shared affiliation, plus approval from two state-level admins.
4. Once approved, the region is live: existing shops inside its boundary appear in it right away, and it gets its own link, featured slots and digest.

## Landscape

Existing services either feed big platforms with stock data or list every kind of business. None offers a curated, character-first way to browse local goods sellers.

| Service | What it does | Gap this project fills |
| --- | --- | --- |
| [Google free local listings](https://support.google.com/business/answer/9934993) | In-store products on Search and Maps, fed by POS data (Pointy) | Exact-product lookup, chains included, ad-funded |
| [NearSt](https://near.st/solution/technology) | Pulls POS stock into Google and Meta | Started as a shopper site, became a data feed for Google |
| [Locally.com](https://join.locally.com/sell-on-locallycom) | Stock search for specialty retail, brand "where to buy" | Built around brand products, not neighborhood character |
| Small apps (Cartmap, shelf., Lowkel, Retlify, FRQ) | Local stock search or marketplaces | Little adoption, thin content, rarely updated |
| [ShopSmallPDX](https://shopsmallpdx.com/small-business-directory) | City-backed directory of 2,000+ Portland small businesses | Logo cards, services mixed with shops, many listings without an address, pandemic-era badges |
| LocalFirst PDX | Portland shop-local platform launched July 2026 | Scope unclear; check before launch as a possible partner |
| Yelp, Facebook pages | Profiles, photos, hours for any business | Public ratings, ads and pay-to-boost, login walls, no goods focus |

What sets this project apart:

- **Curated membership:** only local goods sellers, so every result is a shop you can support
- **Search by thing, not place:** "who might carry something like this" instead of "hardware store near me"
- **No public ratings, ads or pay-to-rank,** and no account needed to browse
- **Place and story:** browsing by street, neighborhood and owner, not isolated listings
- **Community governance and open data,** so it answers to residents and owners, not a platform

Where it is weaker: reach and habit (people already open Google and Yelp) and long-term upkeep. Both are addressed under Operating model.

## Shopper experience

Browsing should feel like window shopping: quick to follow an interest, full of small surprises, and leaving people knowing their neighborhood a little better.

**Ways to wander**

- **Walk a street:** swipe storefront to storefront along a corridor, then step inside a shop page
- **Interest chips:** books, plants, tools, vintage, kids, kitchen, crafts; picked on first visit and stored only in the browser
- **Surprise me:** a shuffle button that jumps to a random shop or block
- **Next door and shops like this:** every page leads to two or three more, so browsing never dead-ends
- **Themes and seasons:** "gifts for gardeners," "holiday markets this weekend," "where to find a pumpkin carving kit"
- **Neighborhood passport:** "you've explored 6 of 24 shops on Alberta," kept on the device, with an optional printable or QR version for in-person visits

**Shop pages**

Photo first: storefront, interior, owner and story, then what they carry, how to visit, hours, phone and "open now." The main actions are **call**, **get directions** and **follow**. A "call to ask" prompt suggests a short script, such as "Do you carry anything like X?"

**Hometown Shelf (product showcase)**

The Hometown Shelf is the heart of window shopping: a curated set of owner-uploaded product photos, the digital version of a shop window display. It shows the range of what a shop carries and calls out what's new or noteworthy.

- **Range shelf:** 6 to 12 photos chosen to represent the breadth of the shop, so a browser understands it at a glance
- **Highlight tags:** each photo can be marked **New**, **Staff pick**, **Local maker**, **Seasonal** or **Just back in**, with a one-line caption and an optional price range
- **Freshness:** "New" tags expire after 21 days and "Just back in" after 14, "Seasonal" ends on the owner's date or after 90 days, and every photo shows when it was added, so the display reads as a snapshot, not a stock promise
- **Across the site:** highlighted products feed the "Fresh from owners" slot, neighborhood digests, follower updates and theme pages, and they make the shop searchable by what it carries
- **Browsing products directly:** shoppers can scroll a neighborhood's newest highlights as a product feed, with every item leading back to its shop page, call and directions

**Search over what shops carry, not live stock**

Shops describe categories, "known for," "you might not expect us to have," and optional featured items. Interior photos can be tagged automatically by an image model. Search matches meaning, not exact product names, so "noise-cancelling headphones" or "canning jars" finds shops likely to carry them or something equivalent. Results say "likely carries" and point to calling or visiting, never to a stock count.

## Featuring and fairness

Every region's home page, from a street up to a state, is built from slots. Each slot is filled by its own rule, so every visit mixes curated, earned and random shops and no shop holds a spot permanently. Rotation, cooldowns and exposure are counted per region.

| Slot | Source | Rotation rule |
| --- | --- | --- |
| Wildcard | Random | Always present; weighted toward shops shown least |
| Community favorites | Shopper votes | Random pick from an eligible pool; cooldown after featuring |
| Fresh from owners | Owner updates (new showcase products, events, photos) | Max one boost per shop per week; meaningful update types only |
| Curated collections | Admins and rotating guest curators | Themes change on a schedule |
| Owner-to-owner picks | Shops recommending other shops | Rotates with the other slots |
| Near you | Location the visitor chooses to share | Distance-based |

**Voting gates** (starting values from [decision 0005](../decisions/0005-featuring-and-freshness-parameters.md))

1. Votes make a shop eligible for the favorites pool; they do not rank it to the top. A shop joins the pool with votes from at least 3 different people in the last 90 days.
2. The favorites slot picks randomly from the pool, weighted from 1× to 2× by vote rate.
3. After being featured, a shop sits out the favorites slot for 60 days.
4. A vote's weight halves every 45 days, so the pool reflects the current season.
5. Votes are normalized to how many people viewed the shop (at least 2 votes per 100 views), so a small shop's regulars count as much as a busy shop's crowd.
6. One vote per person per shop every 30 days, confirmed by an email link with no account, no voting for your own shop, burst detection, and no public vote counts.

Stub pages for unclaimed shops never appear in featured slots.

**Exposure tracking**

The service records how often each shop is shown across all slots. The wildcard slot favors low-exposure shops, and admins get a weekly list of shops that haven't appeared recently. Private shopper feedback such as "great find" can nominate shops for curated features without being shown publicly.

## Owner experience: the storefront builder

Owners build their page by answering a short guided interview, mostly from a phone, and the template handles design. They leave with a polished page they can use as their website or link-in-bio, even if few shoppers browse the directory yet.

Interview steps (each skippable; the page looks good half-finished):

1. **The basics:** name, how to find us, hours, phone, links; pre-filled from public data where possible
2. **The front door:** a storefront photo, with tips on framing
3. **Inside:** 3 to 6 interior photos ("your favorite corner," "a shelf you're proud of")
4. **Who we are:** owner photo and short prompts ("How did this start?", "What do people come back for?")
5. **What we carry:** category tags, "known for," "you might not expect us to have," and the Hometown Shelf product showcase: a range shelf of 6 to 12 product photos plus highlight tags for new and noteworthy items; never stock counts
6. **How to visit:** parking, transit, accessibility, whether calls about stock are welcome

Design choices:

- A fixed structure with a few themes, so every page works in search, maps and walk-a-street
- Phone-first, with autosave and a progress meter ("your storefront is 60% complete")
- **Volunteer-assisted setup:** helpers can draft a page during a storefront day for the owner to review and claim
- **Claiming and verification:** any one of a postcard code mailed to the shop, a call or text to the shop's public number, an email at the shop website's domain, a vouch from a business association or market organizer, or meeting a steward in person. Each page has one primary owner who can invite up to five editors. Disputed claims lock the page while two unconflicted admins decide, and a new owner takes over after the previous owner has 14 days to object ([decision 0002](../decisions/0002-independence-stub-pages-and-claims.md)).
- Owners can export their content and point their own domain at their page

## Hub role

The service helps shops reach customers, keep their loyalty and say what they offer, wherever that happens. It works as a directory for discovery, a publishing tool that turns one owner update into many outputs, and a switchboard to everywhere the shop does business.

| Layer | What it includes | Maintenance cost |
| --- | --- | --- |
| Links out | Website, online store (Shopify, Etsy, Square), Instagram, Facebook, newsletter, Google listing, events, "where else to buy" | Near zero |
| Open formats out | schema.org markup on every page, iCal feeds for markets and events, RSS per shop and per neighborhood, OSM contributions, QR window poster, badge, embeddable widget | Low |
| Two-way syncs | Google Business Profile hours and closures (first); others only with demand and a maintainer | High; APIs change and break silently |

**Loyalty without becoming a social network**

- **Follow this shop** by email or RSS, no shopper account required; owners post short updates from the builder
- **Region digests:** a weekly or monthly email of new shops, events and updates for any region a shopper follows, from one street up to a city
- **Point to the owner's own tools** (newsletter, punch card, Square loyalty) rather than replacing them
- **Minimal shopper data:** follower emails are used only for the updates chosen, never sold, and not shared with owners unless the shopper also joins the shop's own list

## Keeping information current

Three inputs keep pages fresh: owner check-ins, private shopper reports, and admin or volunteer review. Shopper feedback is never shown publicly.

**Owner nudges:** a reminder every 6 months to confirm hours, photos and "how to find us," plus a holiday-hours prompt 14 days before major holidays. A page not confirmed for 12 months shows "may be out of date."

**Private shopper reports**

- Structured types: hours wrong, moved, permanently closed, no longer carries X, photos outdated, phone doesn't work; optional short note
- Routed to the owner first ("2 visitors said your Sunday hours look wrong"); escalated to the region's stewards and moderators after 10 days, or right away when 3 or more independent reports of the same type arrive within 30 days
- Unclaimed pages go straight to the admin queue
- Three independent "permanently closed" reports within 30 days start an admin check, and marking a shop closed needs two admins
- Reporters stay anonymous to owners; light rate limits and verification discourage abuse
- A positive "this was right when I visited" tap refreshes freshness without owner effort

**Public trust signals:** each page shows "last confirmed by owner" and a last-updated date, but never the feedback itself. Interior photos carry their date so nobody reads them as live stock.

## Administration and accountability

Admins will mostly be local business owners and people from business groups, such as district associations or Prosper Portland. Those are the people with the most local knowledge, and also the people most likely to have a stake in which shops get seen. The admin system assumes good intent but is built so that bias is hard to act on and easy to spot.

**Who administers**

- **Scoped to a region.** An admin role belongs to a region, such as Alberta Arts or Portland, and covers that region and everything inside it. A neighborhood steward can't act on another neighborhood.
- **Role types:** region stewards (curation, storefront days, local reports), moderators (content review, eligibility, escalated reports), and region admins (approving new regions and granting roles below them).
- **Declared affiliations.** Every admin records the shops they own, work for or have a financial interest in, plus any organization they represent. Affiliations are visible to all admins.
- **Terms.** Roles last one year and can be renewed, with affiliations confirmed again at each renewal. A role lapses after six months of inactivity. Two admins of the parent region can remove an admin, and an undisclosed conflict is grounds for removal ([decision 0004](../decisions/0004-administration-defaults.md)). Who appoints the first admins is still open.

**The admin action log**

Every admin action is written to a permanent log that every admin can always read.

- **What's recorded:** approving or rejecting eligibility, editing or hiding shop content, removing photos, resolving or dismissing reports, marking a shop closed, changing a claim, creating or editing collections and featured picks, changing rotation settings, approving regions, and granting or removing roles.
- **Each entry shows:** who acted, their role and region, the date and time, the shop or region affected, the before and after values, and a required short reason.
- **Append-only.** No one can edit or delete an entry, including the highest-level admins and the software's own admin tools. Mistakes are fixed with a new entry that refers back to the original.
- **Visible to all admins** at every level, searchable by admin, shop, region, action type and date.
- **Public summary.** Each region publishes a monthly count of admin actions by type, overrides and conflict re-routes, without naming admins or shops.
- **Owners see their own history.** A shop owner can see every admin action taken on their shop, with the reason, though not the identities of shoppers who reported it.
- **Tamper-evident.** Each entry is linked to the one before it, so any gap or alteration can be detected. Periodic copies go to a party outside the admin group, such as the home organization or a public archive.

**Conflict-of-interest rules**

- **No action on your own shop.** Admins can't moderate, feature, curate or resolve reports about a shop they're affiliated with. They manage it through the normal owner tools, like any other owner.
- **No action on competitors.** An admin affiliated with a shop can't take moderation or eligibility action on a shop that competes with it. A competitor is a shop with the same primary category (interest chip) in the same neighborhood or within 1.6 km (1 mile). Admins and owners can also flag a specific competing shop, and the flag stays until an unconflicted moderator removes it.
- **Automatic routing.** When a conflict applies, the system blocks the action and sends it to another eligible admin in the same or a parent region. Admins can also recuse themselves from any item.
- **Two people for drastic actions.** These need a second admin with no affiliation to the shop or its competitors, approving within 7 days:
  - marking a shop closed
  - removing or hiding a listing
  - rejecting eligibility
  - revoking, transferring or deciding a disputed claim
  - hiding all of a shop's photos
  - granting or removing admin roles
  - changing a region's featuring settings
- **No self-featuring.** Curated collections and owner-to-owner picks can't include the curator's own shops. Featuring rules apply to admins' shops exactly as they apply to everyone else's.
- **Overrides are rare and visible.** If no unconflicted admin is available, a parent-region admin can step in, and the override is flagged in the log.
- **Periodic review.** A short regular report shows each admin's actions by type and the shops they touched, so patterns such as repeatedly hiding one shop's photos stand out.

## Data foundation

Public data can seed basic stub pages (name, type, address, hours) so a corridor is populated before owners join. Character content (photos, stories, what they carry) always comes from owners or from volunteers with owner consent.

| Source | Use | Status |
| --- | --- | --- |
| [OpenStreetMap](https://www.openstreetmap.org/copyright) | Base list of shops, types, hours | Use; ODbL requires attribution and sharing improvements back |
| [Oregon Active Businesses](https://catalog.data.gov/dataset/active-businesses-all) | Cross-check, spot newly registered businesses | Use; noisy, no retail tags |
| Shops' own websites | Facts such as hours and address | Facts only; photos and copy are copyrighted |
| ShopSmallPDX, business association and market vendor lists | Seed list and owner contacts | Ask for permission or partnership; don't scrape |
| Google Maps | None | Avoid; terms prohibit extracting places data, and it would conflict with OSM's license |
| Yelp, Instagram | None | Avoid; terms ban scraping, and reusing photos breaks the consent model |

Seeding process:

1. Pull OSM shop tags for the first corridor and cross-check against the state registry.
2. A volunteer walks the corridor to confirm the list, catch closures and new shops, and take storefront photos.
3. Publish unclaimed stub pages with a clear "Is this your shop? Claim it" invitation. Stubs are only for eligible storefronts confirmed open by a volunteer or two independent sources. They show facts only, with a placeholder instead of photos, stay out of featured slots, and come down within 7 days if the owner asks.
4. Contribute corrections back to OSM.

The ODbL obligations and any data-sharing agreement should get a quick review from someone experienced in open-data licensing before launch.

## Operating model

The service is run at the city or neighborhood level as a community project, with low running costs and a stable local home so it outlasts any single volunteer.

- **Home organization:** a business association, neighborhood group, library or co-op that can hold a small budget and own the domain; Prosper Portland and LocalFirst PDX are potential partners
- **Regional growth:** new streets, neighborhoods and cities join as registered regions under the same service; the software stays open source under AGPL-3.0, so a region can run its own instance if it prefers ([decision 0006](../decisions/0006-stack-and-license.md))
- **Low-cost architecture:** pages generated from structured data, photos on inexpensive object storage, a small admin app for the builder, moderation and feedback queues
- **People:** region-scoped admins drawn from shop owners and business groups, region stewards and volunteers for storefront days and in-person checks, rotating guest curators (see Administration and accountability)
- **Reach:** QR posters in shop windows, printed corridor maps, storefront days and events, partner newsletters; physical presence matters more than ads
- **Moderation:** review of bios and photos, eligibility decisions, and handling of escalated reports, all recorded in the admin action log and subject to the conflict-of-interest rules

## Phased roadmap

Start with one corridor done well, then widen features and geography only once the first corridor is lively and maintained. The regional structure and admin accountability are built from the start, even while only one corridor is active.

1. **Phase 0, groundwork:** pick the first corridor, find a home organization, confirm eligibility rules and the first admins and their affiliations, talk to ShopSmallPDX, LocalFirst PDX and the local business association. *Gate:* a partner and 10 or more interested shops.
2. **Phase 1, pilot corridor:** the nested region tree (Oregon, Portland, the pilot neighborhood and corridor), region links and filters, storefront builder, shop pages, links out, schema.org markup, walk-a-street, wildcard and curated slots, private feedback, the admin action log and conflict-of-interest checks, QR window posters, follow by email. Seed from OSM plus a storefront day. *Gate:* 25 or more claimed storefronts and steady visits.
3. **Phase 2, engagement:** community favorites with voting gates, owner updates and digests, interest chips, neighborhood passport, image tagging and "what we carry" search, exposure dashboard. *Gate:* owners updating pages without prompting.
4. **Phase 3, reach and sync:** Google Business Profile sync, calendar and RSS feeds, OSM contribution pipeline, embeddable widgets, community region registration open to outside groups, more corridors and neighborhoods.
5. **Phase 4, regional growth:** more Oregon cities as regions in the same service, plus a packaged playbook and software for places that want their own instance.

## Open questions

Open questions are tracked in the project [to-do list](../../TODO.md), mainly under Conceptual and Organizational.
