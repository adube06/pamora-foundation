# Pamora Testing Strategy

**Version:** 1.0.0

**Status:** Mandatory

**Stability:** Frozen

---

# Purpose

This document defines the testing strategy for Pamora.

Testing exists to verify business correctness, system reliability, security, and maintainability—not merely code coverage.

Every feature is expected to be testable by design.

---

# Testing Philosophy

Testing priorities:

1. Business rules
2. User journeys
3. Security
4. Integrations
5. Performance

Code coverage is a useful metric, but correctness is the primary objective.

---

# Testing Pyramid

```text
            End-to-End
          Integration Tests
      Feature / API Tests
          Unit Tests
```

Target distribution:

* Unit Tests: ~60%
* Feature/API Tests: ~30%
* Integration Tests: ~8%
* End-to-End Tests: ~2%

These percentages are guidance rather than strict requirements.

---

# Unit Tests

Purpose:

Validate isolated business rules.

Examples:

* Budget calculations
* Readiness scoring
* Permission evaluation
* RSVP status transitions
* Expense validation

Unit tests should not depend on external services.

---

# Feature Tests

Purpose:

Validate complete application behavior.

Examples:

* Create Occasion
* Invite member
* Assign task
* Record contribution
* Publish announcement

Feature tests should verify:

* Authorization
* Validation
* Persistence
* Responses
* Events

---

# Integration Tests

Purpose:

Validate communication with infrastructure.

Examples:

* Queue processing
* Storage integration
* Email delivery
* Payment provider adapters
* Calendar synchronization

External providers should be mocked unless explicitly testing sandbox environments.

---

# End-to-End Tests

Purpose:

Validate complete user journeys.

Critical journeys include:

1. Register → Login → Create Occasion
2. Invite Member → Accept Invitation → Join Occasion
3. Create Budget → Record Contribution → Record Expense
4. Request Quotation → Confirm Booking
5. Complete Planning → Complete Occasion

These tests represent the platform's highest-value workflows.

---

# Authorization Tests

Every protected endpoint should verify:

* Authorized access succeeds.
* Unauthorized access fails.
* Forbidden actions return the correct response.

Permissions must never rely solely on frontend enforcement.

---

# Validation Tests

Every request should test:

* Required fields
* Invalid values
* Boundary conditions
* Duplicate submissions
* Business rule violations

---

# Domain Event Tests

Verify that important business actions emit expected events.

Examples:

* OccasionCreated
* TaskCompleted
* ContributionReceived
* BookingConfirmed

Consumers of events should be tested independently.

---

# API Contract Tests

Validate:

* Response structure
* Status codes
* Validation errors
* Pagination
* Authentication requirements

API contracts should remain stable across compatible versions.

---

# Database Tests

Verify:

* Relationships
* Constraints
* Cascade behavior
* Soft deletes
* Audit fields
* UUID generation

---

# Performance Tests

Measure:

* Response times
* Query counts
* Memory usage
* Queue throughput

Performance regressions should be investigated before release.

---

# Security Tests

Include:

* Authorization bypass attempts
* Rate limiting
* CSRF protection (where applicable)
* Input validation
* Injection resistance
* File upload validation

Security testing should be part of every release.

---

# Regression Tests

Every resolved production bug should receive a regression test when practical.

The objective is to prevent the same defect from reappearing.

---

# Test Data

Prefer:

* Factories
* Builders
* Seeded fixtures

Avoid hard-coded test data unless required.

Tests should remain isolated and repeatable.

---

# Continuous Integration

Every pull request must:

* Run automated tests
* Report failures
* Block merging on failed critical checks

No code should reach the main branch with failing mandatory tests.

---

# Coverage Goals

Coverage targets:

* Domain Layer: 90%+
* Application Layer: 80%+
* API Layer: 80%+
* Infrastructure Layer: Risk-based

Coverage should support confidence, not become a goal in itself.

---

# Release Testing Checklist

Before release:

* Unit tests pass
* Feature tests pass
* Integration tests pass
* Critical end-to-end journeys pass
* Security checks complete
* Performance baseline acceptable

---

# Definition of Tested

A feature is considered tested when:

* Acceptance criteria verified
* Business rules validated
* Security reviewed
* Authorization confirmed
* Regression risk addressed
* Automated tests included where appropriate

---

# Architecture Note — Test the Business, Not the Framework (ADR-014)

A key rule for both developers and AI assistants:

Do not write tests because the framework has a certain method.

Write tests to verify business behavior.

Example:

❌ Not very valuable: testing that a controller called a specific method.

✅ Valuable: testing that:

* When a contribution is recorded, the Budget Summary updates.
* When an invitation is accepted, an Occasion Member is created.
* When a booking is confirmed, Vendor Availability changes.
* When a task is completed, a Milestone updates if its conditions are met.

This way, tests stay meaningful even when internal implementation changes. See [ADR-014](../06-decisions/ADR-014-test-the-business.md).

---

# Related Documents

* Engineering Playbook
* Coding Standards
* API Standards
* Security Standards
* Release Plan
