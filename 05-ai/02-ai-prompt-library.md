# Pamora AI Prompt Library

**Version:** 1.0.0

**Status:** Mandatory

**Stability:** Controlled

---

# Purpose

This document contains the standard prompts used when working with AI assistants on the Pamora project.

All prompts assume the AI has already read [`05-ai/01-claude-context.md`](01-claude-context.md).

---

# General Rules

Before responding, the AI should:

1. Understand the requirement.
2. Identify affected domains.
3. Check architectural implications.
4. Consider security.
5. Consider testing.
6. Explain significant trade-offs.
7. Produce maintainable code.

---

# Prompt 01 – New Feature

```text
Implement a new feature for Pamora.

Requirements:
- Follow the Engineering Foundation.
- Follow the Design Foundation.
- Preserve modular architecture.
- Do not introduce shortcuts.
- Explain architectural decisions.
- Include tests.
- Update documentation where necessary.
```

---

# Prompt 02 – Bug Fix

```text
Fix the reported bug.

Requirements:
- Find the root cause.
- Avoid introducing regressions.
- Preserve architecture.
- Add regression tests.
- Explain the cause and the solution.
```

---

# Prompt 03 – Refactoring

```text
Refactor this code.

Requirements:
- Improve readability.
- Reduce duplication.
- Preserve behavior.
- Keep public APIs stable.
- Explain important improvements.
```

---

# Prompt 04 – Code Review

```text
Review this implementation.

Evaluate:

- Architecture
- Maintainability
- Security
- Performance
- Testing
- Readability

Identify risks and recommend improvements.
```

---

# Prompt 05 – Database Design

```text
Design the database changes.

Requirements:

- Follow Database Standards.
- Maintain normalization.
- Add indexes where appropriate.
- Preserve domain ownership.
- Explain relationships.
```

---

# Prompt 06 – Migration Review

```text
Review these migrations.

Verify:

- Naming
- Constraints
- Rollback safety
- Performance
- Compatibility
```

---

# Prompt 07 – API Development

```text
Implement the API.

Requirements:

- Follow API Standards.
- Use proper validation.
- Enforce authorization.
- Return standard responses.
- Include tests.
```

---

# Prompt 08 – React UI

```text
Build the React interface.

Requirements:

- Follow the Design System.
- Follow UI Principles.
- Follow UX Guidelines.
- Ensure accessibility.
- Avoid unnecessary complexity.
```

---

# Prompt 09 – Flutter Screen

```text
Build the Flutter screen.

Requirements:

- Match the React experience.
- Follow the shared Design System.
- Maintain accessibility.
- Optimize performance.
```

---

# Prompt 10 – Security Review

```text
Review this implementation.

Identify:

- Authorization issues
- Authentication issues
- Validation problems
- Sensitive data exposure
- Security improvements
```

---

# Prompt 11 – Performance Review

```text
Evaluate this implementation.

Review:

- Queries
- Memory
- Response time
- Caching
- Scalability
```

---

# Prompt 12 – Test Generation

```text
Generate tests.

Cover:

- Business rules
- Validation
- Authorization
- Edge cases
- Regression risks
```

---

# Prompt 13 – Documentation

```text
Update project documentation.

Requirements:

- Keep terminology consistent.
- Reflect implementation changes.
- Preserve document structure.
```

---

# Prompt 14 – Architecture Review

```text
Evaluate this implementation against the Pamora architecture.

Review:

- DDD
- Modular boundaries
- Coupling
- Events
- Services
- Future scalability
```

---

# Prompt 15 – Release Readiness

```text
Evaluate whether this feature is production ready.

Review:

- Tests
- Documentation
- Security
- Performance
- Deployment implications
- Observability
```

---

# Prompt 16 – Debugging

```text
Diagnose the issue.

Requirements:

- Explain root cause.
- Identify affected domains.
- Recommend the smallest safe fix.
- Prevent recurrence.
```

---

# Prompt 17 – Feature Planning

```text
Before writing code:

- Analyze requirements.
- Identify business rules.
- Identify edge cases.
- Recommend architecture.
- Suggest implementation phases.
```

---

# Prompt 18 – ADR Proposal

```text
An architectural decision is required.

Provide:

- Problem
- Context
- Options
- Recommendation
- Trade-offs
- Consequences
```

---

# Prompt 19 – Dependency Review

```text
Evaluate whether a new dependency should be added.

Review:

- Maintenance
- Security
- Community support
- Performance
- Alternatives
```

---

# Prompt 20 – Production Incident

```text
Investigate a production incident.

Provide:

- Timeline
- Root cause
- Impact
- Resolution
- Preventive actions
```

---

# Prompt Usage Rules

Prefer adapting an existing prompt rather than inventing a new one.

When multiple prompts apply, combine them while preserving the Engineering and Design Foundations.

All outputs should remain consistent with the project architecture.

---

# Architecture Note — Standardize AI Conversations (ADR-024)

The base rule:

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

Using a consistent set of prompts reduces variance in output across different Claude sessions and keeps decisions aligned with the Pamora Foundation. See [ADR-024](../06-decisions/ADR-024-standardize-ai-conversations.md).

---

# Related Documents

* Claude Context
* AI Rules
* Development Workflow
* Engineering Foundation
* Design Foundation
