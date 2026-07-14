# ADR-014 — Test the Business, Not the Framework

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Cross-cutting (Testing Governance)

---

# Context

It is easy — especially for an AI assistant generating tests quickly — to write tests that assert framework mechanics (a controller called a specific method, a specific Eloquent relationship was touched) rather than business outcomes. These tests pass reliably but provide false confidence: they break when implementation details change even though business behavior is unaffected, and they stay green when business behavior breaks as long as the mechanical call still happens.

---

# Decision

Tests must verify business behavior, not framework interaction.

❌ Low value: asserting that a controller called a specific method.

✅ Required: asserting that, for example —

* When a contribution is recorded, the Budget Summary updates.
* When an invitation is accepted, an Occasion Member is created.
* When a booking is confirmed, Vendor Availability changes.
* When a task is completed, a dependent Milestone updates if its conditions are met.

---

# Consequences

* Tests remain valid and meaningful even as internal implementation changes (refactors), which is a prerequisite for the Coding Standards' Refactoring rules ("refactoring should preserve behavior... reduce duplication").
* Domain Event Tests (Testing Strategy) become the natural home for this pattern: assert the event fires, and assert its listeners produce the correct business outcome.
* Raises the bar for what counts as "tested" — a passing test suite that only checks framework wiring does not satisfy this ADR.
* Should be an explicit check in code review per the Coding Standards' Code Review Checklist ("Tests included" must mean business-behavior tests, not method-call assertions).

---

# Related Documents

* [Testing Strategy](../04-engineering/09-testing-strategy.md)
* [Coding Standards](../04-engineering/12-coding-standards.md)
* [AI Development Rules](../05-ai/06-ai-rules.md)
