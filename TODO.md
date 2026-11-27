# Window Walk to-do list

The single list of open work for the project. Updated November 26, 2026.

**How to use it**

- Every item has an ID (C for conceptual, O for organizational, T for technical) so docs, decision records and commits can refer to it, as in "settles C-06."
- Tags show the roadmap phase each item is needed for: **[P0]** groundwork, **[P1]** pilot corridor, **[P2]** engagement, **[P3]** reach and sync.
- When an item is done, tick it and move it to [Done](#done) with the date and a link to the result: a decision record, a doc section or a PoC folder.
- New open questions go here, not into individual docs. Docs link here instead.
- Items settled "by default" have working values in a decision record. They can be revisited, and C-16 schedules that review.

## Conceptual

Product and policy questions to settle. Most end in a [decision record](docs/decisions/).

- [ ] **C-01** Choose the first corridor [P0]. The seed data gives a shortlist, by count of qualifying shops (core / total):
  - **SE Stark St, Montavilla** (about 76th to 82nd): 10 / 12. Montavilla East Tabor Business Association is active.
  - **NE Sandy Blvd, Rose City Park to Roseway** (about 47th to 82nd): 9 / 13
  - **NE Halsey St, Gateway** (about 102nd to 122nd): 6 / 10. Gateway Area Business Association is active, and it's the closest to Parkrose.
  - Parkrose's own stretch of NE Sandy has only 3, too few for a pilot on its own.

  Next: walk each shortlisted corridor (O-07), talk to owners (O-05), and gauge each business association's interest (O-03).
- [ ] **C-07** Decide whether growth beyond Portland happens in one shared service, separate instances, or both [P3]. *Working assumption:* one shared Oregon service, with the software self-hostable for anyone who prefers their own. This decides who governs regions outside Portland, how costs are shared, and whether a statewide home organization is needed.
- [ ] **C-10** Decide who appoints the first admins, and the balance between shop owners, business groups and residents [P0]. Terms, inactivity and removal are set by default in [decision 0004](docs/decisions/0004-administration-defaults.md). Depends on O-03, because the home organization's governance will shape this.
- [ ] **C-17** Decide how corridors that cross neighborhood lines fit the places tree [P1]. Found in the [shopper prototype](poc/shopper-prototype/): NE Sandy runs from Rose City Park into Roseway, and NE Halsey from Hazelwood into Parkrose Heights. Options:
  - a primary neighborhood plus "crosses into" (what the prototype does)
  - corridors as children of the city
  - corridors as community areas
- [ ] **C-18** Decide whether unclaimed pages may fill the wildcard slot during the pilot [P1]. With [decision 0002](docs/decisions/0002-independence-stub-pages-and-claims.md) applied strictly, region pages with few claimed shops have nearly empty featured slots. The prototype controls let you compare both.
- [ ] **C-16** Review the default values after three months of pilot data [P1]:
  - the five-location independence limit and the Oregon/SW Washington rule ([0002](docs/decisions/0002-independence-stub-pages-and-claims.md))
  - the five-shop region minimum ([0003](docs/decisions/0003-region-defaults.md))
  - the competitor rule and the share of actions re-routed ([0004](docs/decisions/0004-administration-defaults.md))
  - favorites thresholds and cooldowns ([0005](docs/decisions/0005-featuring-and-freshness-parameters.md))
  - whether the full admin log should become public

## Organizational

Partners, people, legal and outreach.

**Partners and hosting**

- [ ] **O-01** Find out what LocalFirst PDX offers and who runs it: partner or overlap? [P0]
- [ ] **O-02** Contact Prosper Portland about ShopSmallPDX retail listings and co-promotion [P0]
- [ ] **O-03** Approach a district business association or neighborhood group as a possible home organization. Start with those on the C-01 shortlist: Montavilla East Tabor Business Association and Gateway Area Business Association [P0]
- [ ] **O-04** Reach out to Little Boxes PDX (passport model) and Resourceful PDX (data sharing for used and repair shops) [P1]

**Shops and people**

- [ ] **O-05** Talk to five to ten shop owners on the leading corridor about the storefront builder [P0]
- [ ] **O-06** Recruit the first admins and stewards, and record their affiliations (depends on C-10) [P0]
- [ ] **O-07** Walk the shortlisted corridors to confirm shops, catch closures and unmapped shops, and gauge interest; then plan the first storefront day and recruit volunteers [P0]
- [ ] **O-08** Choose who holds the outside copy of the admin action log. Likely the home organization, so this depends on O-03 [P1]
- [ ] **O-12** Ask business associations and Prosper Portland whether they will vouch for shop owners, using the vouch method in [decision 0002](docs/decisions/0002-independence-stub-pages-and-claims.md) [P1]

**Legal and naming**

- [ ] **O-09** Check domains, USPTO trademarks and the Oregon business registry for Window Walk and Hometown Shelf [P0]
- [ ] **O-10** Get a quick open-data licensing opinion: ODbL obligations, PortlandMaps boundary data terms, and any data-sharing agreements [P1]

## Technical

Proofs of concept, stack choices and build setup. PoCs go in [poc/](poc/).

**Proofs of concept**

- [ ] **T-03** Region tree: nested regions with `ltree` and PostGIS, shop roll-up, region URLs and filters, using the defaults in [decision 0003](docs/decisions/0003-region-defaults.md) [P1]
- [ ] **T-04** Admin action log: append-only table, hash chain, conflict checks, second approvals and routing [P1]
- [ ] **T-05** Fair featuring: simulate slot rotation and exposure across regions, and test the starting values in [decision 0005](docs/decisions/0005-featuring-and-freshness-parameters.md) [P1]
- [ ] **T-06** "What we carry" search: embedding search over shop descriptions [P2]. A vocabulary-based version is in the [shopper prototype](poc/shopper-prototype/) (`/search/`). Next, compare it with embeddings on the same example searches, and log searches that find nothing to see what owners should be prompted to describe.
- [ ] **T-07** Image tagging of interior and shelf photos with a vision model [P2]

**Design and data**

- [ ] **T-11** Design how competitor links are computed, now that C-08 has a default rule [P1]
- [ ] **T-13** Design the claim flow, now that C-15 has default rules: postcard and phone codes, expiry and attempts, editors, disputes, transfers, and handover of volunteer-drafted pages [P1]
- [ ] **T-14** Contribute verified corrections from the seed data back to OpenStreetMap: closed or moved shops, mis-tagged shops and missing chain tags [P1]

**Repo and build**

- [ ] **T-12** Set up the production code folder, CI, contribution guidelines and the AGPL-3.0 LICENSE file when Phase 1 starts. Use the current Astro major version (the prototype uses Astro 5) [P1]
- [ ] **T-16** Decide whether the real service uses Google Street View as a fallback image for unclaimed pages [P1]:
  - Cost: Google charges per image. Terms: images load live and are never stored. Freshness: images are one to four years old.
  - Compare it against illustrations and volunteer photos (O-07) once the prototype has been tried with people (T-15).
  - Mapillary (open license, free key) is still untested as an alternative.
- [ ] **T-15** Try the shopper prototype on real phones and with a few shop owners or neighbors; note what feels like window shopping and what doesn't [P0]
  - Have two or three owners build their own storefront in the builder (`/shop/<slug>/build/`), on their phones, with their own photos. Time it, and note where they stop or skip. Combine this with O-05.

## Done

**Settled by default on 2026-11-26** (see the decision records for values)

- [x] **C-02** Independence and local ownership rules: [decision 0002](docs/decisions/0002-independence-stub-pages-and-claims.md). Which goods qualify: [decision 0001](docs/decisions/0001-eligibility-online-substitutable-goods.md)
- [x] **C-03** What stub pages show and when: [decision 0002](docs/decisions/0002-independence-stub-pages-and-claims.md)
- [x] **C-15** Ownership verification, editors, disputes and transfers: [decision 0002](docs/decisions/0002-independence-stub-pages-and-claims.md)
- [x] **C-04** Region levels, community areas, naming and minimum size: [decision 0003](docs/decisions/0003-region-defaults.md)
- [x] **C-05** Boundary sources, shared areas and disputes: [decision 0003](docs/decisions/0003-region-defaults.md)
- [x] **C-06** Who approves new regions: [decision 0003](docs/decisions/0003-region-defaults.md)
- [x] **C-08** Competitor definition: [decision 0004](docs/decisions/0004-administration-defaults.md)
- [x] **C-09** Drastic actions needing two admins: [decision 0004](docs/decisions/0004-administration-defaults.md)
- [x] **C-11** Admin log visibility: [decision 0004](docs/decisions/0004-administration-defaults.md)
- [x] **C-12** Voting verification: [decision 0005](docs/decisions/0005-featuring-and-freshness-parameters.md)
- [x] **C-13** Favorites thresholds, cooldown and decay: [decision 0005](docs/decisions/0005-featuring-and-freshness-parameters.md)
- [x] **C-14** Tag expiry, nudges and escalation timings: [decision 0005](docs/decisions/0005-featuring-and-freshness-parameters.md)
- [x] **T-08** Public site framework (Astro): [decision 0006](docs/decisions/0006-stack-and-license.md)
- [x] **T-09** API framework and providers: [decision 0006](docs/decisions/0006-stack-and-license.md)
- [x] **O-11** Open-source license (AGPL-3.0): [decision 0006](docs/decisions/0006-stack-and-license.md)

**Completed**

- [x] "What we carry" search in the shopper prototype: products to likely shops, with reasons, searchable by region (2026-11-27)
- [x] Storefront builder in the shopper prototype: claim, six-step interview, progress meter, live preview and publish, all in the browser (2026-11-27)
- [x] Real storefront images in the shopper prototype: Wikimedia Commons photos where available, then Google Street View aimed from each shop's own street (2026-11-27)
- [x] **T-01** Clickable shopper prototype: region pages, walk-a-street for three corridors, claimed and unclaimed shop pages: [poc/shopper-prototype](poc/shopper-prototype/) (2026-11-26)

- [x] **T-02** OSM import and data-quality check for 14 neighborhoods around Parkrose, with candidate corridor counts: [poc/parkrose-seed-data](poc/parkrose-seed-data/) (2026-11-26)
- [x] **T-10** Boundary data source: PortlandMaps `Public/Boundaries` layers 1 and 13; license terms checked under O-10 (2026-11-26)
- [x] Set up the repo structure for docs and proofs of concept (2026-11-26)
- [x] Add regions and admin accountability to the concept and architecture docs (2026-11-26)
- [x] Decide which goods qualify: [decision 0001](docs/decisions/0001-eligibility-online-substitutable-goods.md) (2026-11-26)
