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
