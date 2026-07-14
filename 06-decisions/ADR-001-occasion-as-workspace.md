# ADR-001 — Occasion as Workspace

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Occasion

---

# Context

The Occasion Domain PRD initially describes the Occasion as a business record with attributes, a lifecycle, and permissions. Treated purely as a record, the natural UI is a "details" screen — title, date, location, status — with other domains (Planning, Finance, Marketplace, Communication, Media) bolted on as separate destinations.

That framing undersells what an Occasion actually is: a place where dozens of people coordinate hundreds of small decisions over weeks or months.

---

# Decision

An Occasion is a **Workspace**, not a record.

Opening a single Occasion (e.g. "Amina & John Wedding") opens into a full workspace containing:

```text
Overview
Planning
Committee
Guests
Invitations
Finance
Marketplace
Timeline
Media
Announcements
Activity
Settings
```

In both Flutter and Laravel:

```text
Occasion = Workspace
Workspace = Container for all business domains
```

---

# Consequences

* The Occasion aggregate becomes the natural root for navigation, not just for data ownership — Information Architecture's Occasion Workspace navigation tree derives directly from this decision.
* Every other domain (Planning, Finance, Marketplace, Communication, Media) is modeled as a section *within* the Occasion workspace rather than a sibling top-level feature.
* This is what gives Pamora its intended feel: "a Notion for occasions, a Slack for committees, and an Airbnb for vendors — all within one workspace."
* Engineering must ensure workspace-level authorization (who can see which section) is consistent regardless of entry point.

---

# Related Documents

* [Occasion PRD](../02-product/prd/01-occasion.md)
* [Information Architecture](../03-design/01-information-architecture.md)
* [Domain Model](../04-engineering/04-domain-model.md)
