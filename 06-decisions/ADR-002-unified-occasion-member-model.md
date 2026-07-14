# ADR-002 — Unified OccasionMember Model

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** People, Identity

---

# Context

A naive schema for participants would introduce separate tables per role: `hosts`, `guests`, `committee_members`, and so on. This looks simple in the first months of development, but breaks down once a single person needs to hold different roles across different Occasions — which is the normal case for Pamora, not the exception.

For example, the same person may simultaneously be:

* Host on their own Wedding.
* Treasurer on a friend's wedding.
* Guest on a Birthday.
* Vendor Owner on another Occasion.

Separate per-role tables cannot represent this without duplication and inconsistent permission logic.

---

# Decision

Do not build `hosts`, `guests`, `committee_members` as separate tables.

Instead, the foundation of participation is:

```text
User
    │
    ▼
OccasionMember
    │
    ├── permissions
    ├── responsibilities
    ├── invitation_status
    ├── attendance_status
    └── metadata
```

The `User` (Identity Domain) never changes. What changes is the `OccasionMember` record — the user's membership, permissions, and responsibilities within a specific Occasion (People Domain).

This mirrors the architecture used by Slack (workspace membership), GitHub Organizations (org membership), and Notion (workspace membership).

---

# Consequences

* Identity and People stay cleanly separated — see [ADR-009](ADR-009-identity-separate-from-membership.md), which generalizes this same principle to all roles including Vendor.
* Adding a new responsibility (e.g. "Logistics Lead") is a data change, not a schema change.
* Authorization checks become Occasion-context-dependent by default (see Business Rule BR-039), not based on a global role field on `users`.
* Querying "all Occasions a user participates in, and in what capacity" is a single join through `occasion_members` rather than a union across multiple role tables.

---

# Related Documents

* [People PRD](../02-product/prd/02-people.md)
* [ADR-009 — Identity Is Separate from Membership](ADR-009-identity-separate-from-membership.md)
* [Business Rules](../02-product/05-business-rules.md) — BR-010, BR-011, BR-039
