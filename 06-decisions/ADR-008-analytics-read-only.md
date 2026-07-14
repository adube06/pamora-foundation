# ADR-008 — Analytics Is Read-Only

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Insights

---

# Context

It is tempting to let the Insights Domain "help out" by writing back to other domains — for example, auto-completing a Milestone or adjusting a Budget status directly when it computes that conditions are met. This blurs domain ownership, creates hidden side effects, and makes the system hard to test and reason about.

---

# Decision

The Insights Domain never modifies data owned by other domains. It only reads.

```text
Planning / Finance / Marketplace / People
                │
                ▼
          Domain Events
                │
                ▼
        Insights Engine
                │
                ▼
     Dashboards & Recommendations
```

Insights reads data, calculates KPIs, generates Scores (e.g. Readiness Score, Financial Health), and produces Recommendations — but it never writes to Tasks, Budgets, Bookings, or any other domain's records.

---

# Consequences

* Keeps domain ownership boundaries intact — consistent with the Domain Model's "No domain should directly manipulate another domain's internal state."
* Eliminates an entire class of hidden side effects and makes Insights independently testable.
* Recommendations remain advisory only (per the Insights PRD) — a Milestone still completes because its Planning-owned conditions were met (see [ADR-003](ADR-003-planning-hierarchy.md)), not because Insights decided so.
* Business Rule BR-033 (Readiness Score must always be calculated from live business data, never manually edited) is a direct consequence of this ADR.

---

# Related Documents

* [Insights PRD](../02-product/prd/08-insights.md)
* [Business Rules](../02-product/05-business-rules.md) — BR-033, BR-034
* [ADR-003 — Planning Domain Hierarchy](ADR-003-planning-hierarchy.md)
