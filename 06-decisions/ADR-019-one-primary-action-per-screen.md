# ADR-019 — One Primary Action Per Screen

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** UI Principles (cross-cutting)

---

# Context

An Occasion Workspace exposes many possible actions at once — create a task, add an expense, send an announcement, add a vendor, upload media. Presenting all of them with equal visual weight forces the user to evaluate every option before acting, which raises cognitive load and slows task completion, directly working against the UI Principles' "reduce unnecessary choices" and "guide users toward completion."

---

# Decision

Every screen has exactly one primary action, a small number of secondary actions, and optional contextual actions:

```text
Screen
   │
   ├── Primary Action (1)
   ├── Secondary Actions (few)
   └── Contextual Actions (optional)
```

Example — Occasion Dashboard: **Create Task** is the primary action; Invite Member and View Budget are secondary; Export Report is contextual.

---

# Consequences

* Screen designs must explicitly declare their single primary action before implementation — this becomes part of the Screen Specifications template (once authored) and the Feature Template's "UI / UX Notes" section.
* Prevents the "wall of equal buttons" anti-pattern across the Occasion Workspace, Marketplace, and Admin Portal.
* Requires product/design tradeoffs: when a screen seems to need two equally important actions, that's a signal the screen should be split, not that the rule should bend.
* Composes with [ADR-020](ADR-020-design-for-completion.md) — the primary action is usually the one that moves the user toward completing their current task.

---

# Related Documents

* [UI Principles](../03-design/07-ui-principles.md)
* [Design System](../03-design/03-design-system.md)
