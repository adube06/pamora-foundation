# ADR-027 — Manual Financial Recording During MVP

**Status:** Accepted

**Date:** 2026-07-15

**Domain(s):** Finance

---

# Context

MVP Definition explicitly excludes payment gateway integration from V1.0 (Finance's "Excluded" list: payment gateway integration, automatic reconciliation, installments). That means every Contribution recorded in V1.0 is manually entered by an authorized OccasionMember — a Treasurer types in that an M-Pesa transfer happened; there is no automated verification that it actually did.

This was previously a hidden assumption (audit Finding #13): the Foundation elsewhere emphasizes financial transparency and trust as core principles, but nowhere explicitly stated that V1.0's ledger integrity rests entirely on the honesty and accuracy of whoever records each entry, with no reconciliation process for when a recorded contribution is disputed or wrong. Leaving this implicit risked it being discovered as a trust gap after a real dispute, rather than being a deliberate, documented product decision.

---

# Decision

Until payment gateway integrations become available (Release 1.2, per the Roadmap), financial records in Pamora are manually entered by authorized OccasionMembers.

Trust in V1.0 is established through:

* Audit logs — every Contribution, Pledge, and Expense records who entered it and when (Business Rule BR-036).
* The immutable ledger — entries are not silently editable; corrections happen through new ledger entries, not edits to history (ADR-004).
* Role permissions — only OccasionMembers holding `finance.record_contribution` / `finance.record_expense` (see the [Permission Catalog](../02-product/09-permission-catalog.md)) can create ledger entries at all.

Trust is **not** established through payment verification in V1.0. This is a stated, intentional limitation — not an oversight.

Reconciliation (matching recorded contributions against actual mobile money/bank confirmations) is deferred to Release 1.2, alongside Mobile Money integration, per the Roadmap.

---

# Consequences

* This closes audit Finding #13: the manual-entry limitation is now an explicit product constraint (this ADR), not a hidden assumption.
* Finance PRD and the MVP Definition should describe V1.0 contribution recording as "self-reported, audit-logged" rather than implying any payment verification exists.
* Product/support teams should expect and plan for disputes over recorded-but-unverified contributions in V1.0 — the audit log (who recorded what, when) is the only available evidence when a dispute occurs, not a reconciled bank/mobile-money record.
* When Release 1.2 introduces Mobile Money integration, a follow-up ADR should define the reconciliation process (how a system-confirmed payment relates to a pre-existing manually-recorded Contribution for the same transaction) rather than assuming it is a byproduct of the integration itself.
* This does not change the ledger-first architecture (ADR-004) — manually-entered Contributions are still ledger entries, computed into totals the same way a future gateway-confirmed Contribution would be.

---

# Related Documents

* [Finance PRD](../02-product/prd/04-finance.md)
* [ADR-004 — Financial Ledger Architecture](ADR-004-financial-ledger-architecture.md)
* [MVP Definition](../02-product/02-mvp.md)
* [Roadmap](../02-product/08-roadmap.md) — Release 1.2
* [Permission Catalog](../02-product/09-permission-catalog.md)
