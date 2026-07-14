# ADR-025 — AI Is a Team Member, Not the Architect

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** Cross-cutting (AI Governance)

---

# Context

Because Pamora's primary developer is an AI assistant, there is a risk of the AI's implementation choices becoming the de facto architecture by default — simply because no one pushed back. This inverts the intended relationship: the Foundation documents (Vision, Constitution, Domain Model, ADRs) should shape what the AI builds, not the reverse.

---

# Decision

```text
Human Vision
      │
      ▼
Architecture
      │
      ▼
AI Implementation
      │
      ▼
Review
      │
      ▼
Production
```

AI should help implement the project's vision, not redirect it without approval. Core architectural decisions remain under project governance ([AI Rules](../05-ai/06-ai-rules.md) Rule 17 — "Respect Human Decisions").

---

# Consequences

* Any AI recommendation that would change established architecture (not just extend it) must be raised explicitly and approved — via a new ADR — before implementation, consistent with [ADR-023](ADR-023-ai-assists-architecture-leads.md).
* Code review remains a required step even for AI-authored changes (Development Workflow Phase 7) — AI output is reviewed like any other contribution, not merged automatically on the basis of being AI-generated.
* Positions AI Rules 7 ("Explain Trade-offs") and 19 ("Continuous Improvement") correctly: AI may recommend, but recommendations don't block other work and don't bypass governance.
* Establishes accountability: when architecture changes, a human decision (recorded as an ADR) is the reason, not an unreviewed AI judgment call.

---

# Related Documents

* [AI Rules](../05-ai/06-ai-rules.md)
* [ADR-023 — AI Assists, Architecture Leads](ADR-023-ai-assists-architecture-leads.md)
* [Development Workflow](../05-ai/07-development-workflow.md)
