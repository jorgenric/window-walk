# 0005: Starting values for voting, featuring and freshness

- Status: accepted as default; tune with the featuring simulation (T-05) and pilot data
- Date: 2026-11-26
- Decided by: Eric (defaults proposed by Claude)
- Settles: C-12, C-13, C-14

## Context

The concept describes voting gates, tag expiry, owner nudges and report escalation, but gives ranges or no numbers. These are tuning parameters: changing them later is a settings change, not a redesign.

## Decision

**Voting (C-12)**

- No shopper accounts. A vote is confirmed by a one-time email link.
- One vote per person per shop every **30 days**. Votes are stored against a salted hash of the email, never the address itself.

**Favorites pool (C-13)**

- A shop joins its region's favorites pool when it has votes from **at least 3 different people** in the last 90 days **and** at least **2 votes per 100 page views**.
- The slot picks randomly from the pool, weighted from 1× to 2× by vote rate.
- **Cooldown** after being featured: **60 days**.
- **Vote decay:** a vote's weight halves every **45 days**.

**Hometown Shelf tags (C-14)**

| Tag | Expires |
| --- | --- |
| New | 21 days |
| Just back in | 14 days |
| Seasonal | Owner-set end date, or 90 days |
| Staff pick, Local maker | Never, but always shows the date added |

**Owner nudges (C-14)**

- A confirmation reminder every **6 months**.
- A holiday-hours prompt **14 days** before major US holidays.
- A page whose details haven't been confirmed for **12 months** shows "may be out of date."

**Reports and escalation (C-14)**

- A report goes to the owner first. If it's still open after **10 days**, it escalates to the region's stewards and moderators.
- It escalates right away if **3 or more independent reports** of the same type arrive within 30 days.
- Reports about unclaimed pages go straight to the admin queue.
- **Three independent "permanently closed" reports** within 30 days start an admin check. Marking the shop closed still needs two admins ([decision 0004](0004-administration-defaults.md)).

## Consequences

- The concept's ranges are replaced with these numbers.
- The featuring simulation (T-05) should test the pool threshold and cooldown, which are most likely to need changes in thin regions with few votes.
