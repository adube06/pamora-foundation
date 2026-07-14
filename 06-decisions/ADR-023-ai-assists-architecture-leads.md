# ADR-023 — AI Assists, Architecture Leads

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** Cross-cutting (AI Governance)

---

# Context

An AI assistant generating code quickly can, under time pressure, take the path of least resistance: quietly bending an architectural rule to make a feature easier to implement, rather than flagging the conflict. Without an explicit rule reversing this incentive, "easiest to implement" can slowly override "consistent with the Foundation" across many small decisions.

---

# Decision

The AI's role in any request follows a fixed sequence, and it never reorders steps to skip Foundation checks:

```text
User Request
      │
      ▼
Understand Context
      │
      ▼
Check Foundation Documents
      │
      ▼
Propose Solution
      │
      ▼
Implement
      │
      ▼
Update Documentation
```

AI must not change architecture to make implementation easier. Implementation must follow the existing architecture and standards — not the other way around.

---

# Consequences

* When a request conflicts with the Foundation, the correct move is to pause and propose a new ADR (per [AI Development Rules](../05-ai/06-ai-rules.md) Rule 8/Rule 17), not to quietly reinterpret the existing one.
* Reinforces [ADR-011](ADR-011-code-style-not-optional.md) (architecture and standards are contract, not suggestion) specifically in the context of AI-driven changes.
* Every AI-authored change should be traceable to a Foundation document it followed, making review faster: reviewers check for conformance, not for hidden architectural drift.
* Slows down AI throughput slightly in exchange for long-term codebase stability — an explicit, intentional trade-off given how quickly AI-generated code can accumulate.

---

# Related Documents

* [Claude Context](../05-ai/01-claude-context.md)
* [AI Rules](../05-ai/06-ai-rules.md)
* [ADR-011 — Code Style Is Not Optional](ADR-011-code-style-not-optional.md)
