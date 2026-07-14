# Pamora Deployment Standards

**Version:** 1.0.0

**Status:** Mandatory

---

# Purpose

This document defines the deployment strategy, environments, release process, rollback procedures, and operational requirements for Pamora.

Deployments must be predictable, repeatable, and reversible.

---

# Deployment Principles

* Automate wherever possible.
* Every deployment is traceable.
* Every deployment is reversible.
* Production changes require verification.
* Infrastructure is documented.

---

# Supported Environments

## Local Development

Purpose:

* Feature development
* Debugging
* Unit testing

Characteristics:

* Docker supported
* Local services
* Seeded sample data

---

## Development

Purpose:

* Team integration

Characteristics:

* Shared environment
* Continuous deployment
* Test integrations

---

## Staging

Purpose:

Production-like validation.

Characteristics:

* Same configuration philosophy as production
* Real deployment process
* Performance verification
* User acceptance testing

---

## Production

Purpose:

Serve end users.

Requirements:

* High availability
* Monitoring
* Backups
* Secure configuration
* Restricted access

---

# Release Workflow

```text
Feature Branch
      │
      ▼
Pull Request
      │
      ▼
Automated Tests
      │
      ▼
Code Review
      │
      ▼
Merge to Main
      │
      ▼
Deploy to Development
      │
      ▼
Deploy to Staging
      │
      ▼
Production Approval
      │
      ▼
Production Release
```

---

# CI/CD Requirements

The deployment pipeline must:

* Install dependencies
* Run static analysis
* Run automated tests
* Build frontend assets
* Verify migrations
* Package artifacts
* Deploy safely
* Verify application health

Deployments stop automatically if mandatory checks fail.

---

# Configuration Management

Configuration belongs outside source code.

Use environment-specific configuration for:

* Database connections
* Queue drivers
* Cache drivers
* Mail providers
* Storage providers
* API credentials

Never commit production secrets.

---

# Database Migrations

Rules:

* Migrations are version controlled.
* Deploy schema before dependent code when required.
* Review destructive migrations carefully.
* Backup before high-risk schema changes.

Rollback plans should exist for critical migrations.

---

# Queue Management

During deployment:

* Preserve queued work where practical.
* Restart workers safely.
* Verify worker health after deployment.

---

# Asset Deployment

Frontend assets should:

* Be versioned
* Be cache-friendly
* Support rollback
* Match backend release

---

# Health Checks

Every deployment should verify:

* Application availability
* Database connectivity
* Queue processing
* Cache connectivity
* Storage access
* External integration status (where appropriate)

---

# Rollback Strategy

Rollback triggers include:

* Critical production failures
* Data corruption risk
* Security incidents
* Failed migrations
* Major performance regressions

Rollback procedures must be documented and tested periodically.

---

# Backup Verification

Before significant production releases:

* Confirm recent backups exist.
* Verify restore procedures.
* Record backup status.

A backup that has never been tested is not considered reliable.

---

# Deployment Checklist

Before release:

* Tests passed
* Security review complete
* Documentation updated
* Migrations reviewed
* Rollback plan prepared
* Monitoring configured
* Team notified (where applicable)

After release:

* Health checks passed
* Error rates acceptable
* Performance baseline maintained
* Logs reviewed

---

# Monitoring After Deployment

Monitor:

* Error rates
* Response times
* Queue depth
* Database performance
* Memory usage
* CPU usage
* Failed jobs

Unexpected behaviour should trigger investigation.

---

# Infrastructure Standards

Production infrastructure should include:

* HTTPS
* Reverse proxy (Nginx)
* PHP-FPM
* Redis
* Scheduled backups
* Queue workers
* Log management

Containerized deployments are supported where appropriate.

---

# Disaster Recovery

Document:

* Recovery objectives
* Backup locations
* Restore procedures
* Incident contacts
* Recovery validation steps

Recovery documentation should be reviewed regularly.

---

# Definition of a Successful Deployment

A deployment is successful when:

* The application is available.
* Health checks pass.
* Critical workflows function.
* Monitoring reports normal operation.
* No rollback is required.

---

# Architecture Note — Zero Manual Production Changes (ADR-016)

The base rule of deployment:

* No editing code directly in production.
* No manual database fixes except during an approved incident.
* No secrets committed to the repository.
* Every deployment goes through the same pipeline.

In other words:

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

Production is not a place to experiment with fixes. All changes must start in the repository and pass through the formal deployment process. See [ADR-016](../06-decisions/ADR-016-zero-manual-production-changes.md).

---

# Related Documents

* Release Plan
* Engineering Playbook
* Security Standards
* Observability Standards
* Performance Standards
