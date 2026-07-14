# Pamora Constitution

**Version:** 1.0.0

**Status:** Approved

**Stability:** Frozen

---

# Purpose

This is the supreme governing document of the Pamora Foundation.

Every other document — Vision, Mission, ADRs, the Engineering Playbook, every domain PRD, every design standard — operates within the bounds this Constitution sets. Where any document conflicts with this one, this one wins.

The Constitution does not describe *what* Pamora does (that's Vision and the PRDs) or *how* code should be written (that's the Engineering Playbook). It describes the permanent commitments that no single ADR, PRD update, or implementation decision is allowed to quietly override — the rules that can only change through deliberate constitutional amendment, not routine governance.

---

# Article I — Governing Hierarchy

Implementation must always follow this order of precedence:

1. **This Constitution**
2. AI Master Context
3. Vision, Mission, North Star, Product Philosophy, Product Principles
4. Architecture Decision Records (ADRs)
5. Engineering Playbook and engineering standards (Coding, API, Database, Security, Testing, Deployment, Performance, Observability)
6. Domain PRDs and Business Rules
7. Design standards (Design System, UI Principles, UX Guidelines, Accessibility, Brand Guidelines)
8. Current sprint specification
9. Implementation

No document may contradict a document above it in this order. When a conflict is found, the lower document is wrong and must be corrected — not the higher one.

---

# Article II — The Core Aggregate

**The Occasion is the central aggregate of the entire platform.**

Every business capability, every domain, every permission, every piece of data exists because it serves an Occasion. This is not a design preference; it is the organizing principle the whole domain model depends on. No future domain, feature, or integration may be added that does not ultimately relate to an Occasion.

The Occasion is a **Workspace** (ADR-001) — a container for the business domains that operate within it — not merely a database record.

---

# Article III — Identity and Membership Are Permanently Separate

**A User account carries no role. Role, permission, and responsibility live only on membership records scoped to a single Occasion.**

This is established by ADR-002 (Unified OccasionMember Model) and ADR-009 (Identity Is Separate from Membership). It is foundational to how Pamora supports one person holding different roles across different Occasions, and it is a one-way door: reversing it after real membership data exists would require migrating every permission check in the system. No PRD, ADR, or implementation may introduce role or permission fields on the `User`/Identity entity.

---

# Article IV — Financial Truth Lives in the Ledger

**No business entity may store a derived financial total as a field. All balances, summaries, and totals are computed from source ledger records at read time.**

This is established by ADR-004 (Financial Ledger Architecture). Contributions, Pledges, Expenses, and Budget Items are the source of truth; `remaining_balance`, `total_received`, and equivalents are never stored. This rule exists because Pamora handles other people's money for their most important life events — auditability is not negotiable, and it is far more expensive to retrofit a ledger onto a system that started with denormalized totals than to require this discipline from day one.

---

# Article V — Domains Own Their Data, Exclusively

**No domain may read or write another domain's database tables directly.** Cross-domain interaction happens only through domain events, application services, or defined public contracts (ADR-013).

**External providers are never called directly from business domain code.** Payments, messaging, maps, storage, and calendar providers are accessed only through the Integrations layer (see the Integrations PRD), so that a provider can be replaced without touching business logic.

---

# Article VI — Security Defaults to Deny

**No request reaches business logic before it has been authenticated, then authorized, then validated, in that order** (ADR-015). This applies uniformly across every domain, every API endpoint, and every background job. There is no "low-risk endpoint" exception.

---

# Article VII — The Stability Model Is Constitutional Law

Every document in this Foundation carries a Stability tag: **Frozen**, **Controlled**, or **Living** (see the [README's Stability Model](../../README.md#stability-model)).

* Changing a **Frozen** document requires a new or amended ADR and architectural review. This includes anything this Constitution declares foundational: the domain model, the identity/membership separation, aggregate boundaries, the ledger architecture, and the engineering/security standards that protect them.
* Changing a **Controlled** document requires a documentation update and review, but not an ADR.
* **Living** documents may be updated directly as real user behavior provides evidence.

This three-way distinction is itself a constitutional commitment: it exists so that iteration on UX, screens, and business strategy never requires — or feels like — relitigating the architecture, and so that architecture is never quietly bent to make a UX change more convenient.

---

# Article VIII — AI Assistants Are Bound by This Constitution

Every rule in this document applies equally to human contributors and AI assistants. An AI assistant may recommend, explain trade-offs, and flag risks, but may never unilaterally change a Frozen decision to make an implementation task easier (ADR-023, ADR-025). When a request conflicts with this Constitution, the correct response is to stop and propose an amendment — not to proceed and reinterpret the rule.

---

# Article IX — Amendment Process

This Constitution may only be amended by:

1. Filing an ADR that explicitly proposes a constitutional amendment (not a routine architectural ADR).
2. The ADR must state which Article is being changed and why the original commitment no longer serves the platform.
3. Explicit approval from the project owner. Constitutional amendments carry a higher bar than a standard ADR — they change what is permanently true about Pamora, not what is currently true.

Everything else in the Foundation — new domains, new ADRs, new PRDs, revised business rules — operates *within* these Articles and does not require a constitutional amendment.

---

# Article X — Definition of a Foundation in Good Standing

The Pamora Foundation is in good standing when:

* No two Frozen documents contradict each other.
* Every entity, event, and business rule uses the canonical terminology defined in the Glossary.
* Every Frozen decision traces back to a recorded ADR.
* Every open question discovered during implementation is captured as a new ADR or a documented gap — not silently resolved in code.

---

# Related Documents

* AI Master Context
* Vision
* Domain Model
* Engineering Playbook
* Architecture Decision Records
