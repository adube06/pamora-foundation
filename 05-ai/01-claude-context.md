# Claude Context

**Project:** Pamora

**Version:** 1.0.0

**Status:** Mandatory

---

# Purpose

This document provides the permanent project context that every AI assistant must follow when contributing to Pamora.

It defines the architecture, engineering philosophy, design principles, workflow expectations, and non-negotiable rules.

AI assistants must treat this document as the highest-level project context after the repository source code.

---

# Project Summary

Pamora is a modular event and occasion management platform.

The platform enables users to:

* Create occasions
* Plan activities
* Manage committees
* Track budgets
* Record contributions
* Manage expenses
* Invite guests
* Coordinate vendors
* Share announcements
* Collaborate in real time

Future versions may introduce additional modules while preserving the same architectural principles.

---

# Product Vision

Pamora is designed to become a long-term, scalable platform rather than a collection of isolated features.

Every implementation decision should prioritize maintainability, consistency, and extensibility.

---

# Technology Stack

Backend

* Laravel 12
* PHP 8.4+

Frontend

* React
* TypeScript
* Inertia.js

Admin

* Filament

Mobile

* Flutter

Database

* MySQL

Cache & Queue

* Redis

Storage

* S3-compatible object storage

---

# Architecture

Pamora follows:

* Modular Monolith
* Domain-Driven Design (DDD)
* Clean Architecture
* Event-Driven Communication

Modules should communicate through application services, events, and defined contracts.

Avoid tight coupling.

---

# Engineering Principles

Every contribution must follow:

* Engineering Playbook
* Coding Standards
* API Standards
* Database Standards
* Security Standards
* Testing Strategy
* Deployment Standards
* Performance Standards

If implementation conflicts with these standards, the standards take precedence.

---

# Design Principles

Every UI contribution must follow:

* Design System
* UI Principles
* UX Guidelines
* Accessibility Standards
* Brand Guidelines

Avoid introducing custom UI patterns that bypass the shared design system.

---

# Code Quality Expectations

Code should be:

* Readable
* Modular
* Testable
* Documented where appropriate
* Consistent
* Maintainable

Favor clarity over cleverness.

---

# Development Workflow

Before implementing:

1. Understand the requirement.
2. Identify affected domains.
3. Review existing architecture.
4. Consider security implications.
5. Consider testing implications.

Implementation should not begin without sufficient understanding.

---

# Decision Making

When multiple solutions exist:

Prefer the option that:

* Simplifies maintenance
* Preserves architecture
* Minimizes coupling
* Improves readability
* Scales over time

Avoid optimizing for short-term convenience at the expense of long-term quality.

---

# Pull Requests

Every significant change should include:

* Purpose
* Scope
* Risks
* Testing summary
* Documentation updates

Breaking changes require explicit justification.

---

# AI Behavior Rules

The AI assistant should:

* Explain architectural trade-offs when necessary.
* Ask for clarification when requirements are ambiguous.
* Avoid inventing undocumented business rules.
* Recommend improvements without violating existing standards.
* Highlight potential risks before implementation.

Do not silently change established patterns.

---

# Things to Avoid

Never:

* Introduce unnecessary dependencies.
* Duplicate business logic.
* Bypass validation.
* Ignore authorization.
* Mix unrelated domains.
* Hard-code configuration values.
* Commit secrets.
* Ignore failing tests.

---

# Documentation

Whenever architecture or behavior changes:

Update the relevant documentation before considering the task complete.

Documentation is part of the deliverable.

---

# Definition of Done

A task is complete only when:

* Requirements are satisfied.
* Architecture remains consistent.
* Tests pass.
* Documentation is updated.
* Security considerations are addressed.
* Performance implications are acceptable.

---

# Priority Order

When making decisions, follow this priority:

1. Correctness
2. Security
3. Architecture
4. Maintainability
5. Performance
6. Developer convenience

---

# Architecture Note — AI Assists, Architecture Leads (ADR-023)

The base rule for Claude:

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

AI should not change architecture to make implementation easier. Instead, implementation must follow the existing architecture and standards. See [ADR-023](../06-decisions/ADR-023-ai-assists-architecture-leads.md).

---

# Related Documents

* Project Constitution
* ADR Index
* Engineering Foundation
* Design Foundation
* Product Documentation
