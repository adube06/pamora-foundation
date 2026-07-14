# Pamora Engineering Playbook

**Version:** 1.0.0

**Status:** Mandatory

---

# Purpose

This playbook defines the engineering principles, architectural rules, and development workflow for Pamora.

Every contributor, whether human or AI, must follow this document.

When this playbook conflicts with implementation convenience, the playbook takes precedence unless an approved Architecture Decision Record (ADR) states otherwise.

---

# Engineering Principles

1. Business-first architecture.
2. Domain-driven design (DDD).
3. Modular monolith before microservices.
4. Event-driven communication between domains.
5. Clean Architecture principles.
6. Convention over configuration.
7. Security by default.
8. Testability before optimization.
9. Simplicity over cleverness.
10. Documentation is part of the deliverable.

---

# Technology Stack

## Backend

* PHP 8.4+
* Laravel 12
* MySQL 8+
* Redis
* Laravel Horizon
* Laravel Reverb (real-time)
* Laravel Scout (future search)
* Laravel Pulse
* Laravel Telescope (development only)

## Frontend

* React
* TypeScript
* Vite
* Tailwind CSS

## Mobile

* Flutter

## Infrastructure

* Nginx
* Ubuntu LTS
* Docker (development)
* GitHub Actions
* S3-compatible object storage

---

# Architectural Style

Pamora is a **modular monolith**.

Every business capability belongs to exactly one domain.

Domains communicate through:

* Domain Events
* Application Services
* Public Contracts

Direct cross-domain database access is prohibited.

---

# Folder Structure

```text
app/
├── Domains/
│   ├── Occasion/
│   ├── People/
│   ├── Planning/
│   ├── Finance/
│   ├── Marketplace/
│   ├── Communication/
│   ├── Media/
│   ├── Insights/
│   ├── Identity/
│   └── Integrations/
│
├── Shared/
│
├── Support/
│
└── Console/
```

---

# Domain Rules

Each domain owns:

* Models
* Services
* Policies
* Requests
* Events
* Listeners
* Jobs
* Notifications
* Repositories (only when justified)
* Tests

Domains must not expose internal implementation details.

---

# Application Layers

Within each domain:

```text
Application/
Domain/
Infrastructure/
Presentation/
```

Responsibilities:

* **Presentation**: HTTP, API, CLI.
* **Application**: Use cases and orchestration.
* **Domain**: Business rules.
* **Infrastructure**: Database, queues, storage, external providers.

---

# Database Rules

* Every table has a single owner domain.
* UUIDs are preferred for public identifiers.
* Foreign keys are enforced.
* Soft deletes only where business rules require them.
* Audit fields (`created_by`, `updated_by`) where appropriate.
* Never duplicate derived values unless justified.

---

# API Rules

* REST for external APIs.
* Consistent resource naming.
* Version APIs (`/api/v1`).
* Standard error format.
* Cursor pagination for large datasets.
* Validation at request boundaries.

---

# Event Rules

Business events describe facts that already happened.

Examples:

* OccasionCreated
* TaskCompleted
* ContributionReceived
* BookingConfirmed

Events must:

* Be immutable.
* Use past-tense names.
* Contain only necessary data.

---

# Queue Rules

Use queues for:

* Emails
* Notifications
* Media processing
* Reports
* External integrations

Business-critical writes should remain synchronous unless there is a clear reason otherwise.

---

# Security Rules

* Validate all inputs.
* Authorize every action.
* Never trust client-side data.
* Escape rendered output where required.
* Store secrets outside source code.
* Rotate credentials regularly.

---

# Testing Strategy

Required test types:

* Unit tests
* Feature tests
* Integration tests
* Authorization tests

Critical business workflows must have end-to-end coverage.

---

# Logging

Every critical action should produce structured logs.

Examples:

* User registered.
* Occasion archived.
* Budget exceeded.
* Booking confirmed.

Sensitive information must never be logged.

---

# Performance

* Prevent N+1 queries.
* Use eager loading appropriately.
* Cache expensive reads.
* Paginate large collections.
* Optimize indexes before scaling infrastructure.

---

# Git Workflow

* Feature branches.
* Pull requests.
* Mandatory code review.
* Squash merge into main.
* Semantic commit messages.

Examples:

* feat(finance): add contribution ledger
* fix(planning): prevent duplicate task creation
* refactor(identity): simplify session handling

---

# Documentation

Every feature must include:

* Updated PRD reference (if affected).
* ADR reference (if architectural).
* API documentation (if applicable).
* Tests.
* Migration notes (if database changes).

Code without documentation is considered incomplete.

---

# Definition of Done

A task is complete only when:

* Acceptance criteria pass.
* Tests pass.
* Code review approved.
* Documentation updated.
* No critical security issues remain.
* Performance impact reviewed.
* Monitoring considered where applicable.

---

# Things We Do Not Do

* Business logic in controllers.
* Business logic in views.
* Cross-domain database queries.
* Hidden side effects.
* Hard-coded permissions.
* Magic strings for business states.
* Premature microservices.
* Direct integration calls from business domains.

---

# Engineering Values

* Build for maintainability.
* Prefer clarity over cleverness.
* Design for change.
* Protect business rules.
* Keep the architecture understandable.
* Optimize only after measurement.

---

# AI Development Rules

Because Pamora's primary developer is an AI assistant, the following rules apply specifically to AI-driven development:

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

# Related Documents

* PRDs
* ADRs
* Coding Standards
* API Standards
* Database Standards
* Security Standards
