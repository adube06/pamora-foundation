# ADR-020 — Design for Completion

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** UX Guidelines (cross-cutting)

---

# Context

It is easy to design a screen that presents a form or a piece of information without considering what happens after the user submits it — whether they understand it worked, and whether they know what to do next. This produces flows that technically "work" but leave the user uncertain, which directly undermines the Mission's goal of reducing organizer stress and the North Star's Success Formula (Create → Invite → Plan → ... → Return for the Next Occasion).

---

# Decision

Every important flow is designed end-to-end, not screen-by-screen:

```text
User Starts Task
        │
        ▼
System Guides Progress
        │
        ▼
User Completes Task
        │
        ▼
System Confirms Success
```

Flows such as creating an Occasion, recording a contribution, or sending an invitation must be designed to carry the user all the way to a confirmed completion state — not just present a form or display data.

---

# Consequences

* Every Functional Requirement's Acceptance Criteria (PRD format) should be checked against "does the user receive clear confirmation of completion," not just "was the record created."
* Empty states, loading states, and success confirmations (UI Principles) become mandatory parts of any flow design, not optional polish.
* Works together with [ADR-019](ADR-019-one-primary-action-per-screen.md): the primary action on a screen is usually the one that advances the user toward completion.
* Raises the design bar for MVP scope — a "fast" implementation that skips the completion/confirmation step does not meet this standard, even if the underlying data operation succeeds.

---

# Related Documents

* [UX Guidelines](../03-design/08-ux-guidelines.md)
* [ADR-019 — One Primary Action Per Screen](ADR-019-one-primary-action-per-screen.md)
* [North Star](../00-overview/05-north-star.md)
