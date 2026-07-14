# ADR-016 — Zero Manual Production Changes

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Cross-cutting (Deployment Governance)

---

# Context

Under production pressure, it is tempting to "just fix it live" — edit a file on the server, run a manual SQL statement, patch a config value directly. Each of these bypasses code review, testing, and the audit trail, and is a common root cause of environment drift between what's in Git and what's actually running.

---

# Decision

* No editing code directly in production.
* No manual database fixes, except during an approved incident.
* No secrets committed to the repository.
* Every deployment goes through the same pipeline.

```text
Git
 │
 ▼
CI
 │
 ▼
Tests
 │
 ▼
Build
 │
 ▼
Deploy
 │
 ▼
Production
```

Production is not a place to experiment with fixes. All changes start in the repository and pass through the formal deployment process.

---

# Consequences

* Guarantees that what's running in production always traces back to a specific, reviewed commit — a hard requirement for the Deployment Standards' "every deployment is traceable" principle.
* Incident response must define an explicit "approved incident" exception path (Security Standards' Monitoring & Incident Response) rather than leaving manual fixes as an ungoverned escape hatch.
* Removes an entire class of environment drift bugs ("it works in staging but not in production because someone patched prod directly").
* Raises the bar on CI/CD reliability — since manual intervention isn't an option, the pipeline itself must be trustworthy and fast enough to use even during an incident.

---

# Related Documents

* [Deployment Standards](../04-engineering/10-deployment.md)
* [Security Standards](../04-engineering/08-security.md)
* [Release Plan / Roadmap](../02-product/08-roadmap.md)
