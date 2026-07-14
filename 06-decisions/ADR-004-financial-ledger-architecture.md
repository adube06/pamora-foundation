# ADR-004 — Financial Ledger Architecture

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Finance

---

# Context

A tempting shortcut is to store running totals directly on the `occasions` table — `total_received`, `total_expense`, `remaining_balance`. This is fast to read but creates a second source of truth that can silently drift from the underlying transactions, is hard to audit, and is hard to correct without ad hoc patches.

Business Rule BR-022 already states that financial summaries must be derived from source transactions and must never become the primary source of truth. This ADR formalizes the architecture that satisfies that rule.

---

# Decision

The Finance Domain uses a **ledger-first architecture**. No summary fields (`total_received`, `total_expense`, `remaining_balance`, etc.) are stored on `occasions` or any other table outside Finance.

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

Dashboards compute figures from these source records at read time, using materialized views or caching only as a performance optimization — never as the source of truth.

---

# Consequences

* Every financial figure is fully auditable and reproducible from source transactions at any point in time.
* Correcting a mistake means adjusting the ledger, not patching a cached total — consistent with BR-022 and the Database Standards' "Derived Values" and "Ledger Data" rules (contributions/expenses are append-only).
* Financial reports (Insights Domain) can be regenerated on demand rather than trusted blindly.
* This design is a prerequisite for integrating M-Pesa, Airtel Money, Tigo Pesa, or bank/card gateways later (Revenue Model Phase 3, Release 1.2) — external payment confirmations become new ledger entries, not edits to existing totals.
* Requires disciplined query/caching design so dashboards stay fast despite computing from source records — flagged explicitly as an engineering responsibility, not deferred to "optimize later."

---

# Related Documents

* [Finance PRD](../02-product/prd/04-finance.md)
* [Database Standards](../04-engineering/06-database-blueprint.md) — Derived Values, Ledger Data
* [Business Rules](../02-product/05-business-rules.md) — BR-018 through BR-022
