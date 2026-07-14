# Pamora Development Workflow

**Version:** 1.0.0

**Status:** Mandatory

**Stability:** Frozen

---

# Purpose

This document defines the official development workflow for all work performed on the Pamora project.

The workflow applies equally to human developers and AI assistants.

Every feature, bug fix, refactor, and architectural change should follow this process.

---

# Core Principles

* Understand before implementing.
* Preserve architecture.
* Deliver incrementally.
* Test continuously.
* Document every meaningful change.
* Keep releases safe and predictable.

---

# Phase 1 – Understand the Request

Before writing code:

* Read the task carefully.
* Identify the business objective.
* Clarify ambiguous requirements.
* Determine whether the request introduces new business rules.

Deliverable:

* Shared understanding of the problem.

---

# Phase 2 – Architectural Analysis

Review:

* Affected domains
* Existing services
* Existing UI components
* Database implications
* API implications
* Security implications
* Performance implications

If architectural changes are required, prepare an ADR before implementation.

Deliverable:

* Technical implementation plan.

---

# Phase 3 – Design

If UI changes are involved:

Review:

* Design System
* UI Principles
* UX Guidelines
* Accessibility Standards

Deliverable:

* Implementation approach aligned with the Design Foundation.

---

# Phase 4 – Implementation

Implementation rules:

* Follow Coding Standards.
* Keep commits focused.
* Reuse existing components.
* Avoid duplication.
* Maintain modular boundaries.

Deliverable:

* Working implementation.

---

# Phase 5 – Testing

Verify:

* Business rules
* Validation
* Authorization
* API contracts
* UI behavior
* Edge cases
* Regression risks

Automated tests should be added where appropriate.

Deliverable:

* Verified implementation.

---

# Phase 6 – Documentation

Update documentation when:

* Architecture changes.
* Public APIs change.
* User-facing behavior changes.
* New modules are introduced.
* ADRs are created or modified.

Documentation is part of the feature.

Deliverable:

* Updated repository documentation.

---

# Phase 7 – Code Review

Review checklist:

* Architecture
* Security
* Readability
* Maintainability
* Performance
* Test coverage
* Documentation

Address review feedback before merging.

Deliverable:

* Approved implementation.

---

# Phase 8 – Release Readiness

Verify:

* Tests pass.
* Documentation is current.
* Migrations reviewed.
* Rollback strategy exists.
* Observability is in place.
* Performance budgets remain acceptable.

Deliverable:

* Production-ready change.

---

# Phase 9 – Deployment

Deployment process:

1. Merge to main.
2. Execute CI pipeline.
3. Deploy to Development.
4. Validate.
5. Deploy to Staging.
6. Validate.
7. Deploy to Production.
8. Monitor.

Rollback if critical issues are detected.

---

# Phase 10 – Post-Release

After deployment:

* Monitor logs.
* Review metrics.
* Verify business workflows.
* Record incidents if necessary.
* Capture lessons learned.

Continuous improvement is expected after every release.

---

# Workflow Diagram

```text
Request
   │
   ▼
Understand
   │
   ▼
Architecture Review
   │
   ▼
Design Review
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
Code Review
   │
   ▼
Release Readiness
   │
   ▼
Deployment
   │
   ▼
Monitoring
```

---

# AI Responsibilities

Before generating code, AI should:

* Read relevant Foundation documents.
* Respect existing architecture.
* Explain trade-offs.
* Avoid assumptions.
* Recommend tests.
* Recommend documentation updates.

---

# Human Responsibilities

Project maintainers should:

* Approve architectural changes.
* Review AI output.
* Validate business requirements.
* Approve releases.
* Maintain Foundation documents.

---

# Escalation Rules

Escalate for review when:

* Architecture changes.
* Breaking API changes.
* New dependencies.
* Database restructuring.
* Security-sensitive functionality.
* Large refactors.

---

# Definition of Complete

A task is complete only when:

* Business requirements are satisfied.
* Architecture remains consistent.
* Tests pass.
* Documentation is updated.
* Security has been considered.
* Performance remains acceptable.
* Deployment readiness is confirmed.

---

# Continuous Improvement

The workflow itself should evolve.

Changes to this workflow require:

* Review
* Documentation
* ADR (if architectural)
* Team agreement

---

# Architecture Note — Follow the Workflow, Not Shortcuts (ADR-026)

The final rule of the Foundation:

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

No phase is skipped for the sake of speed. The workflow exists to protect product quality, reduce technical debt, and ensure Pamora can grow for years without losing stability. See [ADR-026](../06-decisions/ADR-026-follow-workflow-not-shortcuts.md).

---

# Related Documents

* Claude Context
* AI Rules
* AI Prompt Library
* Engineering Foundation
* Design Foundation
* ADR Index
