# Pamora Database Standards

**Version:** 1.0.0

**Status:** Mandatory

---

# Purpose

This document defines the standards for database design, schema evolution, naming conventions, integrity rules, and data lifecycle management across Pamora.

Every schema change must comply with these standards.

---

# Database Philosophy

The database is the system of record.

Business truth belongs in normalized domain-owned tables.

Derived values should be calculated or cached intentionally, never duplicated without justification.

---

# Database Engine

Primary database:

* MySQL 8+

Supporting technologies:

* Redis (cache, queues)
* Object Storage (media)
* Search Engine (future)

---

# Domain Ownership

Every table belongs to exactly one domain.

Examples:

```text
Identity
├── users
├── sessions

Occasion
├── occasions

People
├── occasion_members
├── invitations

Planning
├── tasks
├── checklists

Finance
├── budgets
├── contributions
├── expenses
```

No table may be jointly owned by multiple domains.

---

# Naming Conventions

## Tables

Plural snake_case.

Examples:

* occasions
* budget_items
* vendor_services
* reminder_rules

---

## Columns

snake_case.

Examples:

* created_at
* updated_at
* deleted_at
* occasion_id
* budget_category_id

---

## Foreign Keys

Always use:

```text
{table}_id
```

Examples:

* occasion_id
* vendor_id
* task_id

Avoid ambiguous names.

---

# Primary Keys

Internal primary keys:

* BIGINT auto-increment (default)

Public identifiers:

* UUID or ULID exposed externally.

Never expose sequential IDs through public APIs.

---

# UUID Strategy

Every externally addressable entity should include:

```text
id
uuid
```

The application should prefer UUIDs in URLs and APIs.

---

# Foreign Keys

Use foreign key constraints wherever possible.

Benefits:

* Referential integrity
* Safer deletes
* Better documentation
* Fewer orphan records

---

# Cascade Rules

Use cascade deletes only when business rules explicitly allow.

Otherwise prefer:

* Restrict
* Set Null
* Soft Delete

Business rules determine deletion behavior.

---

# Timestamps

Standard timestamps:

* created_at
* updated_at

Soft deletable entities include:

* deleted_at

Avoid custom timestamp names without strong justification.

---

# Audit Fields

Where applicable include:

* created_by
* updated_by
* deleted_by

These reference authenticated users.

Audit history should complement—not replace—activity logs.

---

# Soft Deletes

Use only when recovery is valuable.

Examples:

Suitable:

* Occasions
* Tasks
* Vendors

Usually unnecessary:

* Activity logs
* Ledger entries
* Audit events

---

# Enums

Prefer PHP enums.

Database columns should store stable values.

Avoid embedding business logic into database enum types.

---

# Derived Values

Avoid storing:

* total_expenses
* remaining_budget
* readiness_score

These should be computed or maintained through dedicated projection/caching mechanisms.

---

# Ledger Data

Financial records are append-only where appropriate.

Examples:

* Contributions
* Expenses
* Audit records

Avoid updating historical financial transactions except through approved correction workflows.

---

# Indexing

Index:

* Foreign keys
* UUIDs
* Frequently filtered fields
* Frequently sorted fields

Review indexes periodically.

Avoid unnecessary indexes that slow writes.

---

# Unique Constraints

Use unique constraints to enforce business rules.

Examples:

* Email (when required)
* UUID
* Invitation token

Do not rely solely on application validation.

---

# Activity Logging

Critical business actions should produce immutable activity records.

Examples:

* Occasion created
* Member joined
* Expense recorded
* Booking confirmed

---

# Data Retention

Define retention policies per entity type.

Examples:

* Sessions: short-term
* Audit logs: long-term
* Media: policy-based
* Financial records: retained according to legal and business requirements

---

# Migrations

Rules:

* One logical change per migration.
* Never modify executed migrations.
* Create new migrations for changes.
* Include rollback paths where feasible.

---

# Seeders

Separate:

* Development seeders
* Testing seeders
* Demo seeders

Production seeders should be minimal and intentional.

---

# Performance

Avoid:

* N+1 query patterns
* Large unbounded queries
* Missing indexes
* Excessive joins across domains

Profile before optimizing.

---

# Security

Sensitive fields should be:

* Encrypted where appropriate
* Access controlled
* Excluded from unnecessary serialization

Never store secrets in plain text.

---

# Backup Strategy

Backups must support:

* Point-in-time recovery (where infrastructure permits)
* Regular verification
* Encrypted storage
* Documented restore procedures

---

# Observability

Monitor:

* Slow queries
* Deadlocks
* Connection pool usage
* Migration execution
* Replication status (future)

---

# Definition of a Healthy Schema

A healthy schema is:

* Normalized
* Domain-owned
* Indexed appropriately
* Easy to evolve
* Auditable
* Consistent
* Backward compatible where practical

---

# Architecture Note — Domain-Owned Database (ADR-013)

This is one of the most important principles in Pamora.

```text
Domain
     │
     ▼
Owns Database Tables
     │
     ▼
Publishes Domain Events
     │
     ▼
Other Domains Consume Events
```

Instead of one domain reading another domain's tables directly:

* Finance will not read Planning tables directly.
* Marketplace will not modify Finance tables.
* Communication will not query People internals.

Instead, domains use:

* Public contracts.
* Application services.
* Domain events.
* Read models (where needed).

This prevents tight coupling and keeps the modular monolith clean. See [ADR-013](../06-decisions/ADR-013-domain-owned-database.md).

---

# Related Documents

* Engineering Playbook
* API Standards
* Security Standards
* ADRs
