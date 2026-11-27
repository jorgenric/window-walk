# 0006: Default stack choices and open-source license

- Status: accepted as default; confirm license before accepting outside contributions
- Date: 2026-11-26
- Decided by: Eric (defaults proposed by Claude)
- Settles: T-08, T-09, O-11

## Context

The architecture sketch left framework and provider choices open. The project needs low running costs on a volunteer budget, a mostly static public site, and code that other places can run for themselves.

## Decision

**Stack (T-08, T-09)**

| Piece | Choice | Why |
| --- | --- | --- |
| Public site, builder and admin | **Astro** with the Node adapter: static pages for shops and regions, server-rendered routes and small interactive components for the builder and admin | Mostly-static output is cheap to host and fast on phones; islands cover the interactive parts |
| API | **Fastify** with TypeScript | Built-in schema validation, fast, small |
| Database | **Postgres** with PostGIS, pgvector and `ltree`, on **Render** | One managed database covers regions, search and the region tree |
| Hosting | **Render** for the web app, API, worker and scheduled jobs | Matches the architecture sketch; simple and low cost |
| Photo storage | **Cloudflare R2** | S3-compatible with no download (egress) fees |
| Email | **Postmark** | Reliable delivery for claim codes, nudges and digests |

**License (O-11)**

- **Code:** GNU AGPL-3.0, so anyone who runs a modified version as a public service must share their changes. This keeps the software open for other communities.
- **Shop facts database:** ODbL, as OSM-derived data requires.
- **Owner content** (photos, stories, shelf items) stays the owner's. Owners grant the service permission to display and syndicate it, and can export it at any time.
- Add the LICENSE file when the production code folder is set up (T-12).

## Consequences

- Phase 1 work can start without further stack discussion. Vendors can be swapped later because storage is S3-compatible and the email code sits behind a small interface.
- AGPL puts off some commercial contributors. That suits a civic project, but revisit if a partner organization needs a more permissive license.
