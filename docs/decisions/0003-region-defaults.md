# 0003: Default region levels, boundaries and approvals

- Status: accepted as default
- Date: 2026-11-26
- Decided by: Eric (defaults proposed by Claude)
- Settles: C-04, C-05, C-06; T-10 (data source found)

## Context

The concept makes regions the backbone of the application. Building the region tree (T-03) needs fixed levels, a boundary source, and an approval path. Seeding the Parkrose area also showed that Portland's official layer includes shared areas, and that well-known local names such as Gateway aren't official neighborhoods.

## Decision

**Levels and community areas (C-04)**

- **Standard place levels:** state, city or town, neighborhood, corridor.
- **Optional place levels**, used only where a place needs them: metro or county between state and city, and district between city and neighborhood.
- **Community area types:** business district, market area and theme route. They can overlap any place, but two community areas shouldn't cover substantially the same shops; a parent-region admin judges this.
- **Naming:** places use their official names. Names and slugs must be unique within their parent, and slugs are lowercase and hyphenated.
- **Minimum size:** a region gets its own page, featured slots and digest once it has **five published, eligible shops**. Below that, its shops show as a section of the parent region's page.

**Boundaries (C-05)**

- **Use official government boundaries wherever they're open.** In Portland:
  - neighborhoods from PortlandMaps `Public/Boundaries` layer 1
  - city limits from layer 13
- Elsewhere, use OSM administrative boundaries when no open official layer exists.
- **Shared areas:** Portland's layer includes overlap polygons such as "Roseway/Madison South." Shops in a shared area belong to both neighborhoods, with the first-named one as primary.
- **Disputes:** places always follow the official layer. Local identities that don't match it become community areas. For example, Gateway is a business district spanning parts of Hazelwood, Parkrose Heights and Woodland Park.

**Approvals (C-06)**

- **Corridors and community areas:** a steward proposes, and an admin of the parent region approves.
- **Neighborhoods:** they already exist as official boundaries, and a city-level admin switches one on when it reaches the minimum size.
- **New cities or towns:** they need a local host organization, or at least two stewards with no shared affiliation, plus approval from two state-level admins. Until there are state-level admins, the home organization's admins fill that role.
- Every approval is recorded in the admin action log.

## Consequences

- The region tree can be built and seeded now, starting with Oregon, Portland, the Parkrose-area neighborhoods and whichever corridor C-01 picks.
- Gateway's experience tests whether community areas feel natural to shoppers.
- Adding a new state, and whether growth means one shared service or several instances, stays open (C-07).
- The license terms for PortlandMaps data still need confirming (O-10).
