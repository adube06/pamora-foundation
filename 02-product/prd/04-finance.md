# Finance Domain PRD

**Version:** 1.0.0

**Status:** Approved

---

# 1. Purpose

The Finance Domain manages all financial activities related to an Occasion.

It provides complete visibility into planning finances without attempting to replace full accounting software.

The objective is financial clarity throughout the Occasion lifecycle.

---

# 2. Business Goals

Enable Hosts and authorized Committee Members to:

* Plan budgets.
* Track contributions.
* Monitor expenses.
* Compare planned versus actual costs.
* Understand overall financial readiness.

---

# 3. Scope

The Finance Domain owns:

* Budget
* Budget Categories
* Budget Items
* Pledges
* Contributions
* Expenses
* Financial Summary

It does **not** own:

* Payment Gateway Integrations
* Vendor Services
* Accounting
* Bank Reconciliation

---

# 4. Core Entities

## Budget

Represents the financial plan for an Occasion.

Contains:

* Categories
* Planned Amount
* Current Spending
* Remaining Balance

---

## Budget Category

Examples:

* Venue
* Catering
* Decoration
* Transport
* Photography
* Entertainment
* Miscellaneous

Categories remain configurable.

---

## Budget Item

Represents an individual planned cost.

Example:

Decoration

Estimated Cost:

TZS 800,000

---

## Pledge

Represents a commitment to contribute.

A Pledge is not confirmation that money has been received.

Possible statuses:

* Pending
* Confirmed
* Cancelled
* Expired

---

## Contribution

Represents money actually received.

Possible sources:

* Mobile Money
* Bank Transfer
* Cash
* Card (Future)

Every Contribution may reference a Pledge but is not required to.

---

## Expense

Represents money spent.

Required fields include:

* Amount
* Category
* Date
* Description
* Recorded By

---

# 5. Financial Dashboard

The dashboard should always display:

* Planned Budget
* Total Pledged
* Total Received
* Total Expenses
* Remaining Budget
* Funding Progress
* Spending Progress

Users should understand financial health within seconds.

---

# 6. Functional Requirements

## FR-001 — Create Budget

Priority: Critical

The Host may create a Budget during Occasion setup.

Acceptance Criteria:

* Budget created.
* Default categories available.
* Categories editable.

---

## FR-002 — Add Budget Item

Authorized users may add Budget Items.

---

## FR-003 — Record Pledge

Users may record financial promises.

Pledges should appear immediately within funding progress.

---

## FR-004 — Record Contribution

Authorized users may record received funds.

The platform must distinguish between:

* Promised
* Received

---

## FR-005 — Record Expense

Authorized users may record spending.

Expenses immediately update summaries.

---

## FR-006 — Financial Summary

Financial summaries are calculated dynamically.

They must never become the primary source of truth.

---

# 7. Funding Progress

Funding Progress is calculated from:

```text
Received Contributions
+
Confirmed Pledges
=
Funding Progress
```

Pending Pledges should be displayed separately.

---

# 8. Budget Status

Each Budget may be:

* Under Budget
* On Track
* At Risk
* Over Budget

The status should update automatically.

---

# 9. Domain Events

The Finance Domain emits:

* BudgetCreated
* BudgetUpdated
* PledgeRecorded
* ContributionReceived
* ExpenseRecorded
* BudgetExceeded
* FundingGoalReached

---

# 10. Integrations

Planning Domain

* Budget-related Tasks

Marketplace Domain

* Vendor quotations
* Booking costs

Communication Domain

* Contribution notifications

Insights Domain

* Financial Health Score

---

# 11. Permissions

Capabilities include:

* View Budget
* Edit Budget
* Record Contributions
* Record Expenses
* Export Reports

Permission decisions are based on Occasion Membership.

---

# 12. Reporting

Metrics include:

* Budget Accuracy
* Funding Progress
* Expense Breakdown
* Outstanding Pledges
* Largest Expense Categories
* Cash Flow Timeline

---

# 13. Success Metrics

The Finance Domain succeeds when users can immediately understand:

* How much is needed.
* How much has been promised.
* How much has been received.
* How much has been spent.
* Whether the Occasion remains financially healthy.

---

# 14. Future Enhancements

Future capabilities may include:

* Integrated Mobile Money
* Bank Integration
* Automatic Payment Reconciliation
* Installment Contributions
* Recurring Donations
* Vendor Payment Tracking
* Financial Forecasting
* AI Budget Recommendations

---

# Product Decision — Finance Is Not Accounting

The Finance Domain is not Accounting.

Its goal is not to build QuickBooks or Xero.

Its goal is to answer these questions for the Host:

* How large is our budget?
* How much have we been promised?
* How much have we received?
* How much have we spent?
* How much do we still need?
* Are we financially safe?

This is the "financial operating system" of the Occasion.

---

# Architecture Note — Ledger-First Architecture (ADR-004)

Do not create summary fields such as:

```text
total_received
total_expense
remaining_balance
```

on the `occasions` table.

Instead, the Finance Domain should follow a ledger-first architecture:

```text
Budget
│
├── Budget Items
│
├── Pledges
│
├── Contributions
│
└── Expenses
```

The dashboard then computes (or uses materialized views/caching where needed) from these source records.

Benefits:

* Auditability.
* No data inconsistency.
* Easy to correct mistakes.
* Financial reports can be regenerated at any time.
* Suitable for future integration with M-Pesa, Airtel Money, Tigo Pesa, banks, or other payment gateways.

See [ADR-004](../../06-decisions/ADR-004-financial-ledger-architecture.md).

---

# Related Documents

* Occasion PRD
* Planning PRD
* Marketplace PRD
* Business Rules
* Insights PRD
