# ADR-018 — Tokens Before Components

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** Design System (cross-cutting: React + Flutter)

---

# Context

Pamora ships on two independent client stacks — React (web) and Flutter (mobile) — plus an Admin Portal. Without a shared source of visual truth, each stack tends to hard-code its own color, spacing, and typography values, and the two clients drift apart visually over time even when the underlying components are conceptually the same.

---

# Decision

Design values flow strictly in one direction:

```text
Design Tokens
        │
        ▼
Component Library
        │
        ▼
Pages
        │
        ▼
Features
```

* No component invents its own color, spacing, or typography.
* React and Flutter both consume the same base tokens.
* Changing a token (e.g. Primary Color or Border Radius) updates the look of the entire system without touching every component.

---

# Consequences

* Requires a shared, versioned token source (e.g. a design-tokens package or generated theme files) consumed by both React and Flutter builds — this becomes a dependency of both client codebases.
* A rebrand or visual refresh becomes a token change, not a per-component rewrite — directly supports the Design System's "Definition of a Design System Component."
* Components that hard-code values (a hex color, a pixel spacing value) become code-review flags under the Coding Standards, the same way magic strings and magic numbers already are.
* Slightly higher upfront setup cost (defining the token pipeline) in exchange for long-term visual consistency across web and mobile.

---

# Related Documents

* [Design System](../03-design/03-design-system.md)
* [Coding Standards](../04-engineering/12-coding-standards.md)
