# ADR-003 — Planning Domain Hierarchy

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Planning

---

# Context

Most event apps treat an occasion as `date + invitation`, with a flat task list as the only planning primitive. In reality, an Occasion is hundreds of small coordinated decisions, and a flat list of Tasks cannot communicate real progress — it just grows longer.

---

# Decision

The Planning Domain is not a Task list. It is a four-level hierarchy:

```text
Occasion
    │
    ▼
Planning
    │
    ├── Milestones
    │
    ├── Checklists
    │
    ├── Tasks
    │
    └── Timeline
```

* **Milestone** — a significant checkpoint (e.g. "Venue Confirmed"), achieved automatically when its underlying conditions are met (BR-017).
* **Checklist** — groups related Tasks together (e.g. "Decorations").
* **Task** — the actual unit of work being executed.
* **Timeline** — when things happen, independent of task/checklist grouping.

---

# Consequences

* The Occasion Workspace can show real, structured progress ("Venue Confirmed", "Catering Finalized") instead of an unstructured, ever-growing to-do list — this is the difference between a to-do app and an Occasion Operating System.
* Milestones must be computed from Task/Checklist completion, not manually toggled — this composes with [ADR-008](ADR-008-analytics-read-only.md)'s read-only Insights principle for readiness scoring.
* Engineering must model dependencies between Tasks (e.g. "Pay Deposit" blocks "Decorate Venue") explicitly, per the Planning PRD's Dependencies section.
* Planning Templates (future) generate this full hierarchy per Occasion Type, not just a flat task set.

---

# Related Documents

* [Planning PRD](../02-product/prd/03-planning.md)
* [Business Rules](../02-product/05-business-rules.md) — BR-014 through BR-017
* [ADR-008 — Analytics Is Read-Only](ADR-008-analytics-read-only.md)
