# Pamora Coding Standards

**Version:** 1.0.0

**Status:** Mandatory

---

# Purpose

This document defines the coding conventions for all Pamora codebases.

The goal is consistency, readability, maintainability, and predictable architecture across backend, frontend, mobile, and infrastructure.

---

# General Principles

* Code must be easy to read before it is easy to write.
* Favor explicitness over implicit behavior.
* Small, focused classes and functions.
* One responsibility per class.
* One reason to change per class.
* Avoid duplication.
* Optimize only after measuring.

---

# Naming

## Classes

Use singular PascalCase.

Examples:

* Occasion
* OccasionMember
* Budget
* Contribution
* Vendor

---

## Methods

Use descriptive camelCase verbs.

Examples:

* createOccasion()
* assignMember()
* recordExpense()
* publishAnnouncement()

Avoid:

* doStuff()
* process()
* handleData()

---

## Variables

Use meaningful names.

Good:

```php
$occasion
$budgetItem
$remainingBalance
$acceptedInvitation
```

Avoid:

```php
$data
$temp
$item
$obj
```

---

## Constants

Use UPPER_SNAKE_CASE.

Example:

```php
MAX_UPLOAD_SIZE
DEFAULT_PAGE_SIZE
```

Business states should preferably be implemented as enums instead of string constants.

---

# File Organization

One public class per file.

Filename must match the class name.

Directory structure must follow the domain structure defined in the Engineering Playbook.

---

# PHP Standards

* Follow PSR-12.
* Use typed properties.
* Use return types.
* Prefer constructor property promotion.
* Prefer readonly where applicable.
* Avoid static state.
* Prefer enums over string literals.
* Use value objects for business concepts where appropriate.

---

# Laravel Standards

## Controllers

Controllers should:

* Validate requests.
* Authorize actions.
* Delegate to Application Services.
* Return responses.

Controllers must not contain business rules.

---

## Requests

All validation belongs in Form Request classes.

Never validate directly in controllers.

---

## Models

Models represent business entities.

Avoid placing complex business workflows inside Eloquent models.

---

## Services

Application Services orchestrate use cases.

Business rules remain inside the Domain layer.

---

## Policies

Every protected action must use authorization policies.

Never rely solely on frontend checks.

---

## Events

Events describe completed business actions.

Use past tense:

* OccasionCreated
* ExpenseRecorded
* BookingConfirmed

---

# Database Standards

* Use migrations for every schema change.
* Never edit historical migrations.
* Prefer foreign keys.
* Add indexes intentionally.
* Avoid nullable fields unless justified.
* Use timestamps consistently.

---

# React Standards

* Functional components only.
* TypeScript required.
* Component names in PascalCase.
* Hooks begin with "use".
* Keep components focused.
* Avoid deeply nested state.

---

# Flutter Standards

* Feature-first folder structure.
* StatelessWidget by default.
* State management through approved architecture.
* Strong typing throughout.
* Separate UI from business logic.

---

# Error Handling

* Fail fast.
* Return meaningful messages.
* Never expose internal stack traces to users.
* Log unexpected exceptions.
* Use custom exception types for business errors where appropriate.

---

# Logging

Log:

* Security events.
* Critical business events.
* External integration failures.

Do not log:

* Passwords
* Secrets
* Authentication tokens
* Sensitive personal data

---

# Comments

Prefer expressive code over comments.

Use comments only when explaining:

* Why something exists.
* Non-obvious decisions.
* External constraints.

Avoid comments that simply repeat the code.

---

# Testing Expectations

Every business feature should include:

* Unit tests
* Feature tests
* Authorization tests (where applicable)

Bug fixes should include regression tests whenever feasible.

---

# Code Review Checklist

Reviewers verify:

* Correct architecture.
* Domain ownership respected.
* Tests included.
* Naming consistency.
* Security considerations.
* Performance impact.
* Documentation updates.

---

# Deprecated Practices

The following are not allowed:

* God classes
* Fat controllers
* Hidden side effects
* Copy-paste programming
* Business logic in Blade or React views
* Hard-coded IDs
* Magic numbers
* Magic strings
* Circular dependencies

---

# Refactoring

Refactoring should:

* Preserve behavior.
* Improve clarity.
* Reduce duplication.
* Increase testability.

Avoid large refactors mixed with unrelated feature work.

---

# Definition of Clean Code

Clean code is:

* Predictable.
* Readable.
* Testable.
* Modular.
* Well documented.
* Consistent.
* Easy to extend.

---

# Architecture Note — Code Style Is Not Optional (ADR-011)

In Pamora:

* Architecture is not a suggestion.
* Coding standards are not a suggestion.
* The PRD is not a suggestion.

All three are part of the development contract.

If an implementation violates one of these documents, the change should be blocked until:

* It is brought into compliance with existing standards, or
* It is approved through a new Architecture Decision Record (ADR).

This is how the codebase stays stable even after hundreds of commits and many contributors, human or AI. See [ADR-011](../06-decisions/ADR-011-code-style-not-optional.md).

---

# Related Documents

* Engineering Playbook
* API Standards
* Database Standards
* Security Standards
* ADRs
