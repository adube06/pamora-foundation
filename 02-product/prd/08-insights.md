# Insights Domain PRD

**Version:** 1.0.0

**Status:** Approved

---

# 1. Purpose

The Insights Domain transforms operational data into meaningful information that helps users make better decisions.

It aggregates signals from all business domains to present readiness, financial health, participation, vendor performance, and operational trends.

The domain is analytical in nature and does not own operational business records.

This is the domain that turns data from Planning, Finance, Marketplace, People, and Communication into insights that can actually be acted on — which is what makes Pamora a smart platform rather than an ordinary event management system.

---

# 2. Business Goals

Enable users to:

* Understand Occasion readiness.
* Identify planning bottlenecks.
* Monitor financial health.
* Measure participant engagement.
* Evaluate vendor performance.
* Learn from completed Occasions.

---

# 3. Scope

The Insights Domain owns:

* Dashboards
* KPIs
* Readiness Scoring
* Health Indicators
* Trend Analysis
* Recommendations
* Reports

It does **not** own:

* Tasks
* Budgets
* Bookings
* Media
* User Accounts

---

# 4. Core Concepts

## Readiness Score

A calculated indicator showing overall preparedness for an Occasion.

Inputs may include:

* Task completion
* Milestone completion
* Budget status
* Vendor confirmations
* RSVP completion
* Timeline health

The score is calculated dynamically.

---

## Financial Health

Measures the financial position of an Occasion.

Signals include:

* Budget variance
* Funding progress
* Outstanding pledges
* Expense distribution

---

## Participation Analytics

Measures collaboration.

Examples:

* Invitation acceptance rate
* RSVP rate
* Committee participation
* Task ownership distribution

---

## Vendor Performance

Measures marketplace quality.

Signals include:

* Response time
* Completion rate
* Review scores
* Booking history

---

## Recommendations

Provides actionable suggestions.

Examples:

* "3 critical tasks are overdue."
* "Budget exceeds the planned amount."
* "No confirmed photographer."
* "Invitation response rate is below target."

Recommendations are advisory only and do not modify business data.

---

# 5. Functional Requirements

## FR-001 — Readiness Dashboard

The system shall present an overall Occasion Readiness Score.

Acceptance Criteria:

* Score calculated automatically.
* Supporting factors visible.
* Updated when underlying data changes.

---

## FR-002 — Financial Dashboard

Display funding and spending indicators in near real time.

---

## FR-003 — Participation Dashboard

Display invitation, RSVP, and committee engagement metrics.

---

## FR-004 — Vendor Dashboard

Summarize vendor performance and booking progress.

---

## FR-005 — Historical Reports

Users may review reports from completed Occasions.

Historical reports remain immutable.

---

## FR-006 — Recommendations Panel

Display contextual recommendations based on current data.

Recommendations must explain why they are shown.

---

# 6. Key Performance Indicators

Standard KPIs include:

* Occasion Readiness
* Task Completion Rate
* Milestone Completion Rate
* Budget Utilization
* Funding Progress
* RSVP Completion
* Vendor Confirmation Rate
* Average Response Time

KPIs should be configurable in future releases.

---

# 7. Reports

Available reports include:

* Occasion Summary
* Planning Progress
* Financial Summary
* Vendor Summary
* Participation Summary
* Activity Report

Reports should support export in future releases.

---

# 8. Domain Events

The Insights Domain primarily consumes events from other domains.

Examples:

* TaskCompleted
* BudgetUpdated
* ContributionReceived
* BookingConfirmed
* InvitationAccepted

The domain may emit:

* ReadinessUpdated
* RecommendationGenerated

---

# 9. Integrations

Occasion Domain

* Lifecycle status

Planning Domain

* Tasks
* Milestones

Finance Domain

* Budgets
* Contributions
* Expenses

Marketplace Domain

* Bookings
* Vendor metrics

People Domain

* Membership
* RSVP

Communication Domain

* Delivery statistics

---

# 10. Security

Users may view only analytics for Occasions they are authorized to access.

Aggregated data must respect privacy and permission rules.

---

# 11. Success Metrics

The Insights Domain succeeds when:

* Users identify problems early.
* Planning decisions improve.
* Financial surprises decrease.
* Readiness becomes measurable.
* Completed Occasions provide learning for future planning.

---

# 12. Future Enhancements

Potential capabilities:

* AI-generated planning advice
* Predictive budget forecasting
* Risk scoring
* Smart scheduling suggestions
* Benchmark comparisons
* Cross-Occasion analytics
* Organization-wide dashboards
* Natural language analytics

---

# Architecture Note — Analytics Is Read-Only (ADR-008)

The Insights Domain does not correct data.

The flow must be:

```text
Planning / Finance / Marketplace / People
                │
                ▼
          Domain Events
                │
                ▼
        Insights Engine
                │
                ▼
     Dashboards & Recommendations
```

Therefore:

* Insights reads data.
* It calculates KPIs.
* It generates Scores.
* It provides Recommendations.

But it never modifies Tasks, Budget, Bookings, or Records directly.

This keeps the architecture clean, simplifies testing, and eliminates unexpected side effects. See [ADR-008](../../06-decisions/ADR-008-analytics-read-only.md).

---

# Related Documents

* Planning PRD
* Finance PRD
* Marketplace PRD
* Business Rules
* Information Architecture
