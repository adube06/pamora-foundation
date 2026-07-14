# Changelog

All notable changes to the Pamora Foundation documentation are recorded here.

---

## [1.0.0] — 2026-07-14

### Added

* Initial Pamora Foundation established.
* Overview: AI Master Context, Vision, Mission, Product Philosophy, Glossary, North Star.
* Business: Market Analysis, Customer Personas, Business Model, Value Proposition, Competition Analysis, Revenue Model, Go-To-Market Strategy.
* Product: PRD structure and domain PRDs (Occasion, People, Planning, Finance, Marketplace, Communication, Media, Insights, Identity, Integrations), MVP Definition, User Journeys, Business Rules, Release Plan / Roadmap.
* Design: Information Architecture.
* Engineering: Engineering Playbook, Domain Model, Coding Standards, API Standards, Database Standards, Testing Strategy, Security Standards, Deployment Standards.
* Decisions: ADR-001 through ADR-016.

---

## [1.1.0] — 2026-07-14

### Added

* Engineering: Observability Standards (structured logging, metrics, tracing, health endpoints, alerts, SLOs).
* Decisions: ADR-017 — Every Request Must Be Traceable.

### Changed

* `04-engineering/11-monitoring.md` upgraded from a Draft — Pending stub to the full Observability Standards document.

---

## [1.2.0] — 2026-07-14

### Added

* Engineering: Performance Standards (performance budgets, database/query/caching/queue guidelines, load testing, release gates).
* Design: Design System, UI Principles, UX Guidelines, Brand Guidelines (all mandatory).
* Decisions: ADR-018 (Tokens Before Components), ADR-019 (One Primary Action Per Screen), ADR-020 (Design for Completion), ADR-021 (Accessibility by Default).

### Changed

* `03-design/03-design-system.md` upgraded from a Draft — Pending stub to the full Design System document.
* `03-design/06-accessibility.md` upgraded from a Draft — Pending stub to the full Accessibility Standards document.

---

## [1.3.0] — 2026-07-14

### Added

* AI: Claude Context (`05-ai/01-claude-context.md`) — the primary project context document for AI assistants.
* AI: Pamora AI Prompt Library (`05-ai/02-ai-prompt-library.md`) — 20 standard prompts for recurring work categories.
* AI: Pamora Development Workflow (`05-ai/07-development-workflow.md`) — the mandatory 10-phase process from request to post-release.
* Decisions: ADR-023 (AI Assists, Architecture Leads), ADR-024 (Standardize AI Conversations), ADR-025 (AI Is a Team Member, Not the Architect), ADR-026 (Follow the Workflow, Not Shortcuts). Note: ADR-022 was not provided and is intentionally skipped in this sequence.

### Changed

* `05-ai/06-ai-rules.md` upgraded from the original 10-rule "AI Development Rules" extract to the full, authoritative 20-rule "Pamora AI Rules" document. All existing cross-references to this file remain valid.

### Removed

* `05-ai/01-claude-project-start.md`, `02-claude-feature.md`, `03-claude-review.md`, `04-claude-refactor.md` — placeholder stubs superseded by Claude Context and the AI Prompt Library.

---

## [1.3.1] — 2026-07-14

### Added

* Decisions: ADR-022 — One Brand, Many Platforms. Fills the gap noted in 1.3.0; brand identity now formally extends through Design Tokens to every surface Pamora appears on (web, mobile, admin, documentation, marketing, presentations, emails, social media).

### Changed

* `03-design/09-brand-guidelines.md` — added the Architecture Note cross-referencing ADR-022, matching the pattern already used in the other Design Foundation documents.

---

## [1.4.0] — 2026-07-15

### Added

* README: **Stability Model** section defining `Frozen` / `Living` / `Mixed` as a formal category alongside every document's Version and Status, distinguishing one-way-door decisions (require an ADR to change) from two-way-door decisions (expected to evolve directly from observed user behavior, no ADR required).
* Claude Context: new "Check Stability Before Deciding How to Change a Document" section instructing AI assistants to check a document's Stability tag before proposing how to change it.

### Changed

* Every document across `00-overview/`, `01-business/`, `02-product/` (including all 10 domain PRDs), `03-design/`, `04-engineering/`, and `05-ai/` now carries a `**Stability:**` tag.
  * `00-overview/`, `04-engineering/`, `05-ai/06-ai-rules.md`, `05-ai/07-development-workflow.md`, `05-ai/01-claude-context.md` → **Frozen** (vision/mission/philosophy, all engineering standards, AI governance).
  * `01-business/`, `02-product/02-mvp.md`, `03-feature-catalog.md`, `04-user-journeys.md`, `06-acceptance-criteria.md`, `07-edge-cases.md`, `08-roadmap.md`, `03-design/01-information-architecture.md`, `02-navigation.md`, `04-screen-specifications.md`, `05-components.md`, `05-ai/02-ai-prompt-library.md`, `05-chatgpt-product.md` → **Living** (business strategy, MVP/roadmap sequencing, UX flows and screens, prompt wording).
  * `02-product/00-product-scope.md`, `01-prd.md`, `05-business-rules.md`, all 10 domain PRDs, `03-design/03-design-system.md`, `06-accessibility.md`, `07-ui-principles.md`, `08-ux-guidelines.md`, `09-brand-guidelines.md` → **Frozen**, except `03-design-system.md` which is **Mixed** (token architecture principle Frozen, specific token values Living) and each domain PRD which is Frozen-with-an-inline-note (entities/events/ADRs Frozen; illustrative FR flows Living).
* `02-product/01-prd.md` — added a "Stability Within a Domain PRD" section explaining the split within each domain PRD, referenced from all 10 domain PRD files.

---

## [1.5.0] — 2026-07-15

### Changed

* **Stability Model upgraded from two categories to three: `Frozen` / `Controlled` / `Living`.** The binary model conflated two genuinely different kinds of decision under "Living" — things that evolve purely from observed user behavior (a screen flow) and things that are deliberate business/design calls that still shouldn't be edited casually (a revenue phase, a UI principle). `Controlled` closes that gap: changeable without an ADR, but requires a documentation update plus review, not a silent edit.
* README: Stability Model section rewritten with the three categories and their respective change processes (ADR + architectural review / documentation update + review / direct update).
* Claude Context: "Check Stability Before Deciding How to Change a Document" section rewritten for the three-way split.
* PRD index: "Stability Within a Domain PRD" section rewritten — each domain PRD is now `Mixed` across all three categories (Frozen entities/events, Controlled functional requirements, Living illustrative flows), not just Frozen/Living.
* Re-tagged documents:
  * `01-business/*` (7 files): Living → **Controlled** — business strategy requires deliberate leadership review to revise, not simple observation-driven updates.
  * `02-product/02-mvp.md`, `08-roadmap.md`: Living → **Controlled** — release scope and sequencing decisions need product/leadership review.
  * `02-product/prd/*` (all 10 domain PRDs): Frozen → **Mixed** — each PRD blends Frozen entities/events, Controlled functional requirements, and Living illustrative flows; a single Frozen tag overstated how much of each PRD is actually architecture.
  * `03-design/03-design-system.md`: Mixed (Frozen/Living) → **Mixed (Frozen/Controlled)** — specific token values need design review, not silent edits.
  * `03-design/05-components.md`: Living → **Controlled** — shared component states/variants need design review since changes ripple across both React and Flutter.
  * `03-design/06-accessibility.md`, `07-ui-principles.md`, `08-ux-guidelines.md`, `09-brand-guidelines.md`: Frozen → **Controlled** — durable design philosophy, but not literally domain/aggregate architecture; the specific ADR-backed principles within each (ADR-019, ADR-020, ADR-021, ADR-022) remain Frozen as recorded decisions regardless of the surrounding document's tag.
  * `04-engineering/11-monitoring.md`, `13-performance.md`: Frozen → **Controlled** — the underlying principles (traceability, measure-before-optimizing) stay Frozen via their ADRs, but specific SLOs/budgets are operational numbers meant to be recalibrated against real production evidence.
  * `05-ai/02-ai-prompt-library.md`: Living → **Controlled** — prompt wording changes don't need an ADR, but do need a quick review to avoid team-wide quality regressions.

---

## [1.6.0] — 2026-07-15

### Fixed — architectural audit findings #1 and #2 (blockers)

**#1 — MVP scope contradiction (Marketplace in V1.0 or not).** `02-mvp.md`'s "Included Domains" section listed Marketplace capabilities as part of the base MVP while its own "Recommendation" section deferred Marketplace to V1.1 — and the Roadmap and Customer Personas disagreed with each other about which was correct. Resolved: Marketplace is not part of V1.0.

* `02-product/02-mvp.md` — Marketplace subsection now states "Deferred to Release 1.1. Not part of V1.0" instead of listing included capabilities. Also removed "Vendor profiles" from the Web Application Included list and "Vendor approval" from the Admin Portal Included list (both had nothing to reference without Marketplace present), and reworded Target Users to state Vendor is not a V1.0 persona. The "Recommendation — Slice V1.0 Further" section is retitled "Release Slicing (Adopted)" since it is now the authoritative scope, not a suggestion sitting alongside a contradicting one.
* `01-business/02-customer-personas.md` — "Persona Priority (MVP)" no longer lists Vendor; it now states Vendor is deferred to Release 1.1, with a cross-reference to the Roadmap.
* `02-product/08-roadmap.md` — no change; it was already correct and is now the single source of truth this decision aligns to.

**#2 — Finance ledger contradiction.** `04-finance.md`'s own Budget entity description listed "Current Spending" and "Remaining Balance" as fields the Budget "contains" — directly violating ADR-004 (ledger-first architecture) three sections later in the same document.

* `02-product/prd/04-finance.md` — Budget's stored attributes are now: Budget ID, Occasion ID, Name, Currency, Planned Amount, Status, Created By, Created At. Categories are documented as a relationship (Budget Category is its own entity), not a field. Current Spending, Remaining Balance, Total Received, and Total Expense are explicitly called out as derived values that must never be stored, with a direct pointer to ADR-004.

### Fixed — architectural audit findings #3 and #8 (terminology)

**#3 — "Health Score" vs "Readiness Score."** The Glossary and Business Rules used "Health Score" as the canonical name for the platform's readiness metric; the Insights PRD — the domain that actually owns it — used "Readiness Score" throughout and never used "Health Score" at all. Resolved: **Readiness Score** is canonical, since it required the fewest changes (the owning domain's PRD didn't need to move).

* `00-overview/04-glossary.md` — "Health Score" entry renamed to "Readiness Score"; also now explicitly cross-references the Insights PRD and BR-033, and flags that the "Vendor confirmations" input isn't available until Marketplace ships in Release 1.1.
* `00-overview/00-ai-master-context.md`, `00-overview/03-product-philosophy.md`, `04-engineering/04-domain-model.md`, `02-product/05-business-rules.md` (BR-033), `06-decisions/ADR-008-analytics-read-only.md` — all "Health Score" references renamed to "Readiness Score."
* `02-product/prd/04-finance.md` — "Financial Health Score" corrected to "Financial Health" to match Insights PRD's actual (distinct) sub-metric name, avoiding confusion with the renamed Readiness Score.

**#8 — "Participant" vs "OccasionMember."** Business Rules BR-010 and BR-011 defined "Participant" as if it were the canonical entity name, while ADR-002, ADR-009, and the People PRD all use "OccasionMember." The Glossary defined neither term.

* `02-product/05-business-rules.md` — BR-010 and BR-011 now use "OccasionMember," with BR-010 cross-referencing ADR-002.
* `00-overview/04-glossary.md` — added the missing "OccasionMember" entry (the actual root cause of the ambiguity — the ubiquitous-language document never defined the single most important entity ADR-002 introduced), noting that "Participant" remains acceptable as informal plain-English usage elsewhere in the Foundation.

### Deferred to next round

Findings #4 (Integrations Domain classification), #7 (canonical permission list), #11 (Constitution), and #13 (V1.0 manual-reconciliation limitation) remain open and are intentionally not addressed in this pass.

---

## [2.0.0] — 2026-07-15 — Foundation v1.0 Released

Closes the remaining four audit findings and formally releases the Foundation. Status moves from "Under Active Development" to **Released**, and governance moves to **maintenance mode**.

### Added

* **Constitution** (`04-engineering/01-constitution.md`) — written for the first time, closing Finding #11. The supreme governing document: establishes the full precedence hierarchy (Article I), the Occasion as the permanent core aggregate (Article II), the permanent separation of Identity and Membership (Article III), ledger-first financial truth (Article IV), domain data ownership and the Integrations boundary (Article V), default-deny security (Article VI), the Stability Model as constitutional law (Article VII), AI assistants' binding to the Constitution (Article VIII), the amendment process (Article IX), and the definition of a Foundation in good standing (Article X).
* **ADR-027 — Manual Financial Recording During MVP** (`06-decisions/ADR-027-manual-financial-recording-during-mvp.md`) — closes Finding #13. States explicitly that V1.0 Contributions are self-reported and audit-logged, not payment-verified, and that trust rests on audit logs, the immutable ledger, and role permissions until Release 1.2 introduces Mobile Money integration. Cross-referenced from Finance PRD's FR-004.
* **Canonical Permission Catalog** (`02-product/09-permission-catalog.md`) — closes Finding #7. One `{domain}.{action}` string per capability across all 9 Core Business Domains plus Platform Administration, replacing the informal, inconsistent permission examples scattered across each domain PRD. Tagged Frozen — it is an authorization contract. Cross-referenced from People PRD Section 7.

### Changed

* **Integrations reclassified as a Supporting Technical Domain, not a Core Business Domain** — closes Finding #4. `04-engineering/04-domain-model.md` now explicitly separates the 9 Core Business Domains from Integrations, with a new Section 10 explaining the classification (it owns no business data or business rules, in DDD terms it is a supporting/generic subdomain) and why it doesn't appear in the Domain Relationships diagram. `02-product/01-prd.md` and `02-product/prd/10-integrations.md` cross-reference the same classification.
* README — "Repository Status" now reads **Released** instead of "Under Active Development." New "Foundation Governance Mode" section: no more speculative Foundation documents; changes only via new ADR or implementation-discovered issue; Frozen/Controlled documents follow their normal governance process; Living documents update freely from real usage.
* Claude Context — new "Foundation Is in Maintenance Mode" section instructing AI assistants not to add Foundation content speculatively going forward.

### Foundation status

All 15 findings from the architectural audit are now resolved or explicitly and durably documented (#13 via ADR-027). The Foundation has moved from well-structured documentation to an internally consistent, governed architecture repository: no known contradictions between Frozen documents, canonical terminology throughout, every foundational commitment traceable to an ADR. Primary effort moves to `pamora-app`.
