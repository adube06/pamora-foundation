# ADR-024 — Standardize AI Conversations

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** Cross-cutting (AI Governance)

---

# Context

Different AI sessions, given the same task phrased differently, can produce meaningfully different results — different scope, different depth of testing, different documentation follow-through. Without a shared set of starting prompts, output quality and consistency depend heavily on how well each individual prompt happens to be worded.

---

# Decision

Pamora maintains a standard [AI Prompt Library](../05-ai/02-ai-prompt-library.md) covering the recurring categories of work (new feature, bug fix, refactor, code review, database design, API development, UI work, security review, performance review, test generation, documentation, architecture review, release readiness, debugging, feature planning, ADR proposals, dependency review, production incidents).

```text
Standard Prompt
       │
       ▼
Consistent AI Behaviour
       │
       ▼
Consistent Code Quality
       │
       ▼
Consistent Architecture
```

Using a consistent set of prompts reduces variance in output across different Claude sessions and keeps decisions aligned with the Pamora Foundation.

---

# Consequences

* New work should start by adapting an existing prompt from the library rather than writing one from scratch (Prompt Usage Rules).
* Reduces the chance that a session skips a step (e.g. forgetting to ask for tests, or for a documentation update) simply because the prompt didn't mention it.
* The library itself becomes a maintained artifact — when a new recurring task category emerges, it should be added to the library rather than solved ad hoc each time.
* Does not replace judgment: Prompt Usage Rules explicitly allow combining prompts, and [Claude Context](../05-ai/01-claude-context.md)'s AI Behavior Rules still require explaining trade-offs and flagging ambiguity.

---

# Related Documents

* [AI Prompt Library](../05-ai/02-ai-prompt-library.md)
* [Claude Context](../05-ai/01-claude-context.md)
