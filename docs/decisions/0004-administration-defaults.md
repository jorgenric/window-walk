# 0004: Default administration rules: competitors, drastic actions, terms and log visibility

- Status: accepted as default; revisit after three months of pilot data
- Date: 2026-11-26
- Decided by: Eric (defaults proposed by Claude)
- Settles: C-08, C-09, C-11; part of C-10

## Context

The admin action log and the conflict-of-interest checks are in Phase 1 scope, so they need working definitions. A conflict only re-routes an action to another admin; it doesn't block the work. That makes a broad competitor rule cheap.

## Decision

**Competitors (C-08)**

- Two shops compete when they **share their primary interest chip** (tools, home, books and so on) **and** are in the same neighborhood or within **1.6 km (1 mile)** of each other.
- Shops that sell many kinds of goods, such as grocers, variety stores and thrift shops, are compared by primary chip only.
- Admins and owners can also **flag** a specific competing shop. A flag stays in place until an unconflicted moderator removes it.
- Review after three months: if conflicts re-route more than about a fifth of all actions, narrow the rule.

**Drastic actions needing a second unconflicted admin (C-09)**

- Marking a shop closed
- Removing or hiding a listing
- Rejecting eligibility
- Revoking or transferring a claim, and resolving a disputed claim
- Hiding all of a shop's photos
- Granting or removing admin roles
- Changing a region's featuring or rotation settings

A second approval must come within **7 days** or the request expires. Everyday actions don't need one: fixing a typo, hiding a single photo, resolving a report, or editing a collection.

**Admin terms (part of C-10)**

- Roles last **one year** and can be renewed.
- Affiliations must be declared before an admin's first action and confirmed again at renewal.
- A role lapses after **six months** without any admin action.
- Two admins of the parent region can remove an admin, and the removal is logged with a reason. An undisclosed conflict found later is grounds for removal.

**Log visibility (C-11)**

- **Full entries:** visible to all admins, and to a shop's owner for entries about that shop.
- **Public summary:** a monthly report for each region, published on the site. It counts actions by type, overrides, and actions re-routed for conflicts, without naming admins or shops.
- Review after the pilot whether the full log should also be public, perhaps with some delay.

## Consequences

- The admin action service and competitor computation (T-04, T-11) can be built against these rules.
- **Still open in C-10:** who appoints the first admins, and the balance between shop owners, business groups and residents. Both depend on the home organization (O-03).
