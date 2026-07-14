# ADR-017 — Every Request Must Be Traceable

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** Cross-cutting (Observability Governance)

---

# Context

Without observability, debugging production is guesswork. A support report like "the Contribution never showed up" spans multiple layers — an HTTP request, a queued job, one or more Domain Events, possibly an external integration callback — and without a consistent identifier threading through all of them, reconstructing what happened requires reproducing the issue rather than simply reading the trail it already left.

---

# Decision

Every user action must be traceable end-to-end via a propagated Request ID / Correlation ID:

```text
User Action
      │
      ▼
Request ID
      │
      ▼
Application Logs
      │
      ▼
Queue Jobs
      │
      ▼
Domain Events
      │
      ▼
External Integrations
      │
      ▼
Completion
```

The identifier must propagate through HTTP requests, queued jobs, scheduled jobs, and external integration calls — not stop at the boundary of the original request.

---

# Consequences

* Structured logs (Observability Standards) must include Request ID and Correlation ID on every entry, not just at the API layer.
* Queue jobs and listeners triggered by Domain Events (see [ADR-006](ADR-006-event-driven-communication.md)) must carry the originating Request ID forward, which requires this to be designed into the job/event payload from the start, not retrofitted.
* Support and on-call debugging shifts from "reproduce the bug" to "look up the trace" — directly reducing Mean Time to Detection and Mean Time to Recovery (Observability Standards' Objectives).
* Integrations Domain webhook handlers (Integrations PRD) must accept and log correlation identifiers where the external provider supports it, and generate one internally where it doesn't.

---

# Related Documents

* [Observability Standards](../04-engineering/11-monitoring.md)
* [ADR-006 — Event-Driven Communication](ADR-006-event-driven-communication.md)
* [Integrations PRD](../02-product/prd/10-integrations.md)
