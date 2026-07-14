# ADR-021 — Accessibility by Default

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** Accessibility (cross-cutting)

---

# Context

Accessibility is frequently treated as a post-launch enhancement — something to "add later" once core features ship. Retrofitting accessibility after implementation is significantly more expensive than designing for it from the start, and Pamora's own Product Philosophy already commits to designing for growth into markets and user bases the MVP doesn't yet serve.

---

# Decision

Accessibility is not a feature to be added later. It is considered at every stage of delivery:

```text
Design
   │
   ▼
Accessibility Review
   │
   ▼
Implementation
   │
   ▼
Testing
   │
   ▼
Release
```

---

# Consequences

* Accessibility is a required non-functional requirement even for MVP scope (already stated in the MVP Definition's Non-Functional Requirements as "basic accessibility") — this ADR extends that into a mandatory process gate, not just a checklist item.
* Screen and component specifications must include accessibility considerations (keyboard behavior, focus behavior, screen-reader expectations) before implementation begins, per the Accessibility Standards' "Accessibility Documentation" section.
* Testing Strategy's release checklist should treat accessibility testing (keyboard, screen reader, contrast) as a release gate, alongside security and performance checks.
* Even though Pamora launches in Tanzania first, building to these standards from day one avoids costly retrofits as the platform expands to new markets and user bases (Vision's Geographic Vision).

---

# Related Documents

* [Accessibility Standards](../03-design/06-accessibility.md)
* [MVP Definition](../02-product/02-mvp.md)
* [Testing Strategy](../04-engineering/09-testing-strategy.md)
