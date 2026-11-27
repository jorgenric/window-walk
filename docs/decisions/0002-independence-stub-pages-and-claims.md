# 0002: Default rules for independence, stub pages and ownership claims

- Status: accepted as default; revisit after three months of pilot data
- Date: 2026-11-26
- Decided by: Eric (defaults proposed by Claude)
- Settles: C-02, C-03, C-15

## Context

Phase 1 needs working rules for three related questions: which shops count as independent, what an unclaimed page may show, and how someone proves they run a shop. None of these could wait for a partner organization, and all are easy to tighten or loosen later.

## Decision

**Independent and local (C-02)**

- A shop counts as independent when it is not a franchise or a location of a chain, its owners are based in Oregon or SW Washington, and it has **no more than five retail locations**.
- Members of retailer co-ops or buying groups (True Value, Ace, Do it Best) and dealers for particular brands still count as independent. Ownership, not the sign, decides.
- Local nonprofit shops count, such as library bookstores and pet thrift stores. Large regional charity chains with more than five stores don't.
- **Verification:** the owner attests to independence when claiming. A moderator checks the Oregon business registry record. Unclear cases go to the region's moderators, and rejecting a shop is a drastic action that needs a second unconflicted admin ([decision 0004](0004-administration-defaults.md)).

**Stub pages before a claim (C-03)**

- Stub pages are published only for **eligible storefront shops** confirmed open by a volunteer visit or by two independent sources, such as OSM plus the shop's own website.
- A stub shows: name, category, address and neighborhood, hours and phone when they come from OSM or the shop's own site, a website link, an **Unclaimed** label, a "last checked" date, data attribution and a **Claim this shop** button.
- A stub doesn't show photos, stories or a Hometown Shelf. It uses a neutral illustrated placeholder until the owner claims the page, or agrees in person during a storefront day.
- Stubs appear in lists, maps, search and walk-a-street, but **not in any featured slot**.
- **Opt-out:** an owner can ask for their stub to be removed. It is hidden within 7 days, logged, and not republished unless the owner claims it.
- Studio, home-based and market sellers never get stubs. Their pages exist only when the seller creates them.

**Ownership claims (C-15)**

- **Any one of these verifies a claim:**
  1. A code on a postcard mailed to the shop address (expires after 30 days)
  2. A code by phone call or text to the shop's public number, as recorded before the claim started from OSM, the shop's website or a volunteer visit (expires after 15 minutes)
  3. An email to an address at the domain of the shop's own website
  4. A vouch from an approved business association or market organizer
  5. Meeting a steward in person at the shop or a storefront day
- Each claim allows five code attempts. Every verified claim is recorded in the admin action log.
- **Several people:** each page has one primary owner, who can invite up to five editors. Editors can edit content but can't transfer ownership or delete the page.
- **Disputed claims:** a competing claim on a claimed page locks the page to its current content. Both parties verify again with a different method, and two unconflicted admins decide within 14 days.
- **Change of hands:** a new owner claims as usual. The previous owner is emailed, and ownership transfers if they don't object within 14 days.
- **Home-based sellers** verify by vouch, market organizer, or an Oregon business registry record plus a video call with a steward. No street address is ever stored.

## Consequences

- Corridors can be populated before owners join, without showing anything an owner hasn't agreed to beyond public facts.
- The five-location limit and the Oregon/SW Washington rule are guesses, so check them against real edge cases in the pilot (Milwaukie Lumber, with three yards, passes; Goodwill doesn't).
- The claim flow design (T-13) can now go ahead.
