# ADR-012 — APIs Are Contracts

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Cross-cutting (API Governance)

---

# Context

Pamora has three independent clients of the backend: the React web app, the Flutter mobile app, and the Admin Portal. Without an explicit ownership rule, it is easy for frontend teams to informally dictate API shape ("just add this field for us") or for backend changes to break clients silently, because no single party is accountable for API stability.

---

# Decision

* React does not own the API.
* Flutter does not own the API.
* The backend does not own the UI.

The API itself is the contract that connects all three. Any change that breaks the contract requires either a new API version (`/api/v2`) or a documented backward-compatibility plan — never a silent breaking change.

---

# Consequences

* API Standards (response envelope, status codes, pagination, versioning) apply uniformly regardless of which client is consuming the endpoint.
* Breaking changes are visible and deliberate — gated by the API Versioning rule, not slipped in through a "minor" endpoint tweak.
* Mobile (Flutter) and Web (React) can evolve independently as long as they respect the current contract version, which matters given Flutter release cycles are typically slower than web deploys.
* Requires API documentation (OpenAPI recommended) to be treated as a deliverable, per the API Standards' "Definition of a Production-Ready API."

---

# Related Documents

* [API Standards](../04-engineering/07-api-specification.md)
* [Engineering Playbook](../04-engineering/02-engineering-playbook.md)
