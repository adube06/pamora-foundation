# Pamora AI Rules

**Version:** 1.0.0

**Status:** Mandatory

---

# Purpose

This document defines the mandatory rules that every AI assistant must follow when contributing to the Pamora codebase.

These rules exist to protect the architecture, maintain code quality, and ensure long-term consistency.

This supersedes and expands the original 10-item "AI Development Rules" list first defined in the [Engineering Playbook](../04-engineering/02-engineering-playbook.md); those 10 rules remain valid and are folded into the 20 below.

---

# Rule 1 – Architecture First

Architecture always takes precedence over implementation convenience.

AI must never recommend shortcuts that violate:

* Modular Monolith architecture
* Domain-Driven Design
* Clean Architecture
* Established ADRs

---

# Rule 2 – Read Before Writing

Before generating code, AI should:

1. Understand the requirement.
2. Read relevant documentation.
3. Identify affected modules.
4. Review existing patterns.
5. Consider future maintainability.

Never generate code without context.

---

# Rule 3 – Preserve Domain Boundaries

Modules communicate only through approved interfaces:

* Application Services
* Domain Events
* Public Contracts

AI must not introduce cross-domain coupling.

---

# Rule 4 – Do Not Duplicate Logic

Before implementing:

* Search for existing services.
* Search for existing actions.
* Search for reusable components.

Prefer reuse over duplication.

---

# Rule 5 – Security by Default

Every implementation should include:

* Validation
* Authorization
* Error handling
* Secure defaults

Never assume frontend validation is sufficient.

---

# Rule 6 – Test Significant Changes

AI should recommend or generate tests for:

* Business rules
* APIs
* Permissions
* Edge cases
* Regressions

Large changes should not be delivered without testing guidance.

---

# Rule 7 – Explain Trade-offs

When multiple valid approaches exist, AI should explain:

* Advantages
* Disadvantages
* Long-term implications

Avoid presenting opinion as fact.

---

# Rule 8 – Respect Existing Patterns

Prefer consistency with the existing codebase over introducing a new style.

If an established pattern is inadequate, recommend an ADR rather than silently replacing it.

---

# Rule 9 – Documentation is Part of the Feature

When behavior, architecture, or public interfaces change:

* Update relevant Markdown documentation.
* Update ADRs if required.
* Keep terminology consistent.

A feature is incomplete if documentation is outdated.

---

# Rule 10 – Avoid Premature Optimization

Optimize only when:

* A measurable problem exists.
* The change preserves maintainability.
* Performance evidence supports the decision.

---

# Rule 11 – Minimize Dependencies

Before adding a dependency, evaluate:

* Maintenance status
* Community support
* Security history
* Existing alternatives

Prefer the platform's existing capabilities whenever practical.

---

# Rule 12 – Never Guess Business Rules

If requirements are unclear:

* Ask clarifying questions, or
* Clearly state assumptions.

Do not invent product behavior.

---

# Rule 13 – Preserve Backward Compatibility

Avoid breaking:

* Public APIs
* Shared contracts
* Database compatibility
* Existing workflows

Breaking changes require explicit approval and documentation.

---

# Rule 14 – Keep Commits Focused

Suggested commit scope:

* One feature
* One fix
* One refactor
* One documentation update

Avoid combining unrelated work.

---

# Rule 15 – Think Beyond the Current Task

Before completing work, evaluate:

* Security impact
* Performance impact
* Testing impact
* Documentation impact
* Future scalability

---

# Rule 16 – Prefer Simplicity

The simplest correct solution should generally be preferred.

Avoid unnecessary abstraction unless it clearly improves maintainability.

---

# Rule 17 – Respect Human Decisions

Architectural decisions made by the project maintainers override AI preferences.

AI supports decision-making but does not replace project governance.

---

# Rule 18 – Production Mindset

Every implementation should be written as though it may reach production.

Avoid "temporary" code unless explicitly marked, documented, and approved.

---

# Rule 19 – Continuous Improvement

When appropriate, AI may recommend:

* Refactoring opportunities
* Documentation improvements
* Test improvements
* Performance enhancements

Recommendations should not block unrelated work unless they address critical risks.

---

# Rule 20 – Definition of AI Success

An AI contribution is successful when it:

* Solves the requested problem.
* Preserves architecture.
* Improves maintainability.
* Protects security.
* Includes appropriate testing guidance.
* Keeps documentation current.

---

# Architecture Note — AI Is a Team Member, Not the Architect (ADR-025)

The core rule:

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

AI should help implement the project's vision, not redirect it without approval. Core architectural decisions remain under project governance. See [ADR-025](../06-decisions/ADR-025-ai-team-member-not-architect.md).

---

# Related Documents

* Claude Context
* AI Prompt Library
* Development Workflow
* Engineering Foundation
* Design Foundation
