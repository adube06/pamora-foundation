# ADR-010 — Release Philosophy

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Cross-cutting (Release Process)

---

# Context

A common startup failure mode is attempting to build many features in parallel before shipping anything usable, which delays real user feedback and lets scope drift unchecked. Pamora spans nine business domains and a two-sided marketplace; without an explicit release philosophy, it would be easy to try to ship all of it at once.

---

# Decision

Pamora ships in strictly sequential, complete stages — never partial ones:

```text
Foundation
      │
      ▼
Internal Alpha
      │
      ▼
Public MVP
      │
      ▼
Marketplace
      │
      ▼
Payments
      │
      ▼
AI Platform
      │
      ▼
Organization Platform
```

Every stage must be:

* Deployable
* Testable
* Usable
* Measurable

No release is ever "50% complete."

---

# Consequences

* Forces hard scope discipline per release — this is what produced the further MVP slicing recommendation in the [MVP Definition](../02-product/02-mvp.md) (V1.0 Core → V1.1 Marketplace → V1.2 Payments → V2.0 Intelligent Platform).
* Marketplace and Payments are explicitly deferred past the first public release, even though they are core to the long-term Business Model — validated demand from Hosts must exist before Marketplace liquidity is worth building for (Go-To-Market Strategy's Marketplace Liquidity Strategy).
* Each release's Exit Criteria (Release Plan) becomes a hard gate, not a suggestion — a release cannot move to the next stage without meeting it.
* Requires the team (human or AI) to resist scope creep within a release in favor of shipping the current stage completely.

---

# Related Documents

* [Release Plan / Roadmap](../02-product/08-roadmap.md)
* [MVP Definition](../02-product/02-mvp.md)
* [Go-To-Market Strategy](../01-business/07-go-to-market.md)
