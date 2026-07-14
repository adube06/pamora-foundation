# ADR-026 — Follow the Workflow, Not Shortcuts

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** Cross-cutting (Process Governance)

---

# Context

Under time pressure, it's tempting to skip a phase of the development process — ship without updating documentation, merge without the full review checklist, deploy without confirming rollback readiness. Each individual skip feels harmless; accumulated across many changes, they are how technical debt and inconsistent quality actually accumulate.

---

# Decision

Every change — feature, bug fix, refactor, or architectural change — follows the full [Development Workflow](../05-ai/07-development-workflow.md) without skipping phases:

```text
Idea
 │
 ▼
Understand
 │
 ▼
Architecture
 │
 ▼
Design
 │
 ▼
Implementation
 │
 ▼
Testing
 │
 ▼
Documentation
 │
 ▼
Review
 │
 ▼
Deployment
 │
 ▼
Monitoring
```

No phase is skipped for the sake of speed.

---

# Consequences

* The Development Workflow's "Definition of Complete" becomes a hard gate, not a checklist to reference loosely — matching the standard already set by [ADR-011](ADR-011-code-style-not-optional.md) for code and architecture.
* Escalation Rules (architecture changes, breaking API changes, new dependencies, database restructuring, security-sensitive functionality, large refactors) must trigger the full workflow, not an abbreviated version.
* Protects the compounding value of everything else in this Foundation: standards, ADRs, and testing/security/performance gates only work if they're actually followed on every change, not just the ones that feel important at the time.
* This is the final governing rule of the Foundation — it exists specifically to keep Pamora able to grow for years without losing stability, per the Vision's long-term scalability goals.

---

# Related Documents

* [Development Workflow](../05-ai/07-development-workflow.md)
* [ADR-011 — Code Style Is Not Optional](ADR-011-code-style-not-optional.md)
* [Vision](../00-overview/01-vision.md)
