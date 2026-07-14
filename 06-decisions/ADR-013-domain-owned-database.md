# ADR-013 — Domain-Owned Database

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Cross-cutting (Database Governance)

---

# Context

In a modular monolith, the single biggest risk to maintainability is domains quietly reaching into each other's tables — Finance joining directly against `tasks`, Marketplace updating `budgets` directly, Communication querying People's internal tables. Each shortcut is individually convenient and collectively turns the "modular" monolith into a tightly coupled one that is as hard to change as a poorly-factored single codebase.

---

# Decision

Every table belongs to exactly one domain. Cross-domain interaction never happens through direct database access.

```text
Domain
     │
     ▼
Owns Database Tables
     │
     ▼
Publishes Domain Events
     │
     ▼
Other Domains Consume Events
```

Instead of reading another domain's tables directly, domains use:

* Public contracts.
* Application services.
* Domain events.
* Read models (where needed).

Concretely: Finance will not read Planning tables directly; Marketplace will not modify Finance tables; Communication will not query People internals.

---

# Consequences

* Preserves the modular monolith's ability to be decomposed into services later, if ever needed, without a full rewrite.
* Forces domain boundaries to be explicit in code, not just in documentation — direct cross-domain queries become a code review red flag per the Engineering Playbook's "Things We Do Not Do" (cross-domain database queries).
* Increases short-term implementation effort for cross-domain features (e.g. a Finance dashboard showing Marketplace booking costs must go through a defined interface, not a join).
* Works in tandem with [ADR-004](ADR-004-financial-ledger-architecture.md) (ledger-first Finance) and [ADR-006](ADR-006-event-driven-communication.md) (event-driven Communication) as concrete instances of this same principle.

---

# Related Documents

* [Database Standards](../04-engineering/06-database-blueprint.md)
* [Domain Model](../04-engineering/04-domain-model.md)
* [Engineering Playbook](../04-engineering/02-engineering-playbook.md)
