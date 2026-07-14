# ADR-009 — Identity Is Separate from Membership

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Identity, People

---

# Context

It is common — and tempting — to store a "role" field directly on the `users` table (e.g. `role: host`). This breaks down immediately in Pamora, because a person's role is never global: the same person is a Host on one Occasion, a Guest on another, a Treasurer on a third, and possibly a Vendor Owner on a fourth. A role field on `users` cannot represent this without becoming meaningless or requiring constant overwriting.

---

# Decision

Identity and Membership are fully separate domains. No roles or permissions are stored on `users`.

```text
User
   │
   ▼
Identity Domain
   │
   ▼
Occasion Membership (People Domain)
   │
   ▼
Permissions
```

A `User` (Identity Domain) has exactly one account. All context-specific permissions and responsibilities live in `OccasionMember` records (People Domain), scoped per Occasion — see [ADR-002](ADR-002-unified-occasion-member-model.md).

Example: Amina has one Pamora account. She is Host on Wedding A, Guest on Funeral B, Treasurer on Graduation C, and Vendor Owner on Business D — all through the same account, differentiated entirely by membership records, not by account-level role fields.

---

# Consequences

* The `users` table stays domain-agnostic: authentication, verification, and profile only (Identity PRD Scope).
* Authorization decisions are Occasion-context-dependent by default (Business Rule BR-039), not based on a global role.
* This is a prerequisite for Multi-workspace, Multi-organization, Vendor Portal, and Enterprise Edition (Release 3.0 Organization Platform) — those all become new membership contexts, not new user types.
* Every domain that needs to check "can this user do X" must resolve it through the relevant OccasionMember (or future OrganizationMember) record, not through a `user.role` shortcut — this must be enforced in Coding Standards code review (Policies section).

---

# Related Documents

* [Identity PRD](../02-product/prd/09-identity.md)
* [ADR-002 — Unified OccasionMember Model](ADR-002-unified-occasion-member-model.md)
* [Business Rules](../02-product/05-business-rules.md) — BR-039
