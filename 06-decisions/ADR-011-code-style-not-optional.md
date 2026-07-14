# ADR-011 — Code Style Is Not Optional

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Cross-cutting (Engineering Governance)

---

# Context

Documentation-driven development only works if the documentation is actually binding. Without an explicit governance rule, it is easy for architecture, coding standards, and PRDs to be treated as guidance that can be quietly bypassed under deadline pressure — especially by an AI assistant generating code quickly across many domains.

---

# Decision

In Pamora:

* Architecture is not a suggestion.
* Coding standards are not a suggestion.
* The PRD is not a suggestion.

All three are part of the development contract. If an implementation violates one of these documents, the change must be blocked until either:

1. It is brought into compliance with the existing standard, or
2. It is approved through a new Architecture Decision Record (ADR).

---

# Consequences

* Code review (human or AI) must treat Coding Standards, the Engineering Playbook, and domain PRDs as hard gates, not style preferences — see the Coding Standards' Code Review Checklist.
* Any deliberate deviation from a standing document requires a new ADR before merging, not after — this is the formal escape hatch referenced in [AI Development Rules](../05-ai/06-ai-rules.md) rule 10.
* Keeps the codebase stable across hundreds of commits and many contributors (human or AI), which is the explicit goal stated in the Coding Standards.
* Raises the cost of "just this once" shortcuts — intentionally, since those shortcuts are what erode a modular monolith into an unmaintainable one over time.

---

# Related Documents

* [Coding Standards](../04-engineering/12-coding-standards.md)
* [Engineering Playbook](../04-engineering/02-engineering-playbook.md)
* [AI Development Rules](../05-ai/06-ai-rules.md)
