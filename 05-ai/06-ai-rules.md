# AI Development Rules

**Version:** 1.0.0

**Status:** Mandatory

---

# Purpose

These rules apply specifically to AI-driven development on Pamora, since the platform's primary developer is an AI assistant (Claude). They supplement — and do not replace — the [Engineering Playbook](../04-engineering/02-engineering-playbook.md) and [AI Master Context](../00-overview/00-ai-master-context.md).

---

# The Rules

1. Never invent business rules.
2. Always reference the relevant PRD before implementing a feature.
3. Do not create new tables or enums without checking existing domain models.
4. Do not bypass domain events.
5. Do not duplicate business logic across domains.
6. Keep pull requests focused on one feature or bug.
7. Write tests for every business rule change.
8. Update documentation alongside code changes.
9. Prefer extension over modification where practical.
10. If implementation conflicts with the Foundation, stop and propose an ADR instead of proceeding.

---

# Why These Rules Exist

An AI assistant can generate large amounts of plausible-looking code quickly. Without explicit constraints, that speed can silently drift the codebase away from the documented business rules, domain boundaries, and architecture — exactly the failure mode this Foundation exists to prevent.

Each rule above maps to a specific risk:

* Rules 1–2 prevent invented behavior that was never approved in a PRD.
* Rules 3–5 prevent architecture drift across domain boundaries (see [Domain Model](../04-engineering/04-domain-model.md) and [ADR-013](../06-decisions/ADR-013-domain-owned-database.md)).
* Rules 6–8 keep changes reviewable and the documentation trustworthy.
* Rule 9 favors additive, low-risk change over risky rewrites.
* Rule 10 is the escape hatch: when the Foundation and the request conflict, the correct move is to pause and propose an ADR, not to guess.

---

# Related Documents

* AI Master Context
* Engineering Playbook
* Coding Standards
* Architecture Decision Records
