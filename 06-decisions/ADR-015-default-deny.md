# ADR-015 — Default Deny

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Cross-cutting (Security Governance)

---

# Context

Security bugs most often occur at boundaries: an endpoint that forgets an authorization check, a form that trusts client-side validation, a background job that assumes its input is already safe. Without one consistently applied rule, every domain risks reinventing (and occasionally forgetting) its own request-handling discipline.

---

# Decision

No request reaches business logic before passing, in strict order:

```text
Request
   │
   ▼
Authenticated?
   │
   ├── No → Reject
   │
   ▼
Authorized?
   │
   ├── No → Reject
   │
   ▼
Validated?
   │
   ├── No → Reject
   │
   ▼
Execute Business Logic
```

This is a default-deny pipeline: authentication, then authorization, then validation, always in that order, applied uniformly across every domain.

---

# Consequences

* Establishes one rule enforced consistently rather than per-domain security judgment calls — directly operationalizes the Security Standards' "Authorization... Deny by default" and "Zero trust" principles.
* Controllers stay disciplined: validate, authorize, delegate — never skip a step because "this endpoint is low-risk" (Coding Standards' Controllers section).
* Client-side permission checks (React, Flutter) are UX only; the server is always the enforcement point (Security Standards' Authorization rules — "never trust client-side permissions").
* Makes security review mechanical and auditable: any endpoint can be checked against this exact three-step pipeline.

---

# Related Documents

* [Security Standards](../04-engineering/08-security.md)
* [API Standards](../04-engineering/07-api-specification.md)
* [Engineering Playbook](../04-engineering/02-engineering-playbook.md)
