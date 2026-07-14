# Pamora Observability Standards

**Version:** 1.0.0

**Status:** Mandatory

**Stability:** Controlled — the request-traceability principle ([ADR-017](../06-decisions/ADR-017-request-traceability.md)) is Frozen; specific SLO numbers, alert thresholds, and tooling choices are Controlled and expected to be recalibrated against real production evidence.

---

# Purpose

This document defines how Pamora measures, monitors, traces, and diagnoses system behavior across all environments.

Observability enables engineering teams to understand what the system is doing without reproducing issues locally.

---

# Objectives

* Detect problems early.
* Reduce Mean Time to Detection (MTTD).
* Reduce Mean Time to Recovery (MTTR).
* Improve production reliability.
* Provide actionable operational insights.

---

# Pillars of Observability

Pamora is built on four pillars:

1. Logs
2. Metrics
3. Traces
4. Events

Together they provide complete operational visibility.

---

# Structured Logging

All application logs must be structured.

Every log entry should include:

* Timestamp
* Log level
* Service name
* Environment
* Request ID
* Correlation ID
* User ID (when applicable)
* Occasion UUID (when applicable)
* Domain
* Action
* Message

Sensitive information must never appear in logs.

---

# Log Levels

Use consistent severity levels:

* DEBUG
* INFO
* NOTICE
* WARNING
* ERROR
* CRITICAL

Examples:

DEBUG

* Cache miss

INFO

* Occasion created

WARNING

* Slow query detected

ERROR

* Payment provider unavailable

CRITICAL

* Database unreachable

---

# Metrics

Every deployment should expose operational metrics.

Infrastructure Metrics

* CPU usage
* Memory usage
* Disk usage
* Network traffic

Application Metrics

* Requests per second
* Response times
* Error rates
* Queue depth
* Failed jobs
* Cache hit ratio

Business Metrics

* Occasions created
* Tasks completed
* Contributions recorded
* Vendor bookings
* Active users

---

# Distributed Tracing

Every request should be traceable across components.

Trace identifiers should propagate through:

* HTTP requests
* Queue jobs
* Scheduled jobs
* External integrations

A single user action should be traceable end-to-end.

---

# Domain Events

Critical business events should be observable.

Examples:

* OccasionCreated
* InvitationAccepted
* TaskCompleted
* ContributionReceived
* BookingConfirmed

Events should include metadata required for troubleshooting.

---

# Health Endpoints

Expose dedicated health checks.

Recommended endpoints:

```text
/health
/health/live
/health/ready
```

Checks should verify:

* Database
* Cache
* Queue
* Storage
* External dependencies (where appropriate)

---

# Alerts

Alerts should be actionable.

Alert categories:

* Availability
* Error rate
* Queue backlog
* Database failures
* Storage failures
* Authentication anomalies
* Integration failures

Avoid noisy alerts.

Every alert should define:

* Trigger
* Severity
* Owner
* Expected response

---

# Dashboard Standards

Engineering dashboards should display:

System Health

* Availability
* Error rate
* Response time

Application Health

* Active users
* Queue status
* Failed jobs
* API latency

Business Health

* New occasions
* Invitations sent
* Budget activity
* Marketplace bookings

---

# Error Tracking

Every unexpected exception should include:

* Stack trace
* Request ID
* Environment
* Release version
* Domain
* User context (where permitted)

Duplicate errors should be grouped automatically.

---

# Audit vs Observability

Audit Logs

Purpose:

* Compliance
* Historical accountability

Observability Logs

Purpose:

* Diagnostics
* Performance
* Reliability

These concerns must remain separate.

---

# Incident Timeline

Every major incident should produce a timeline containing:

* Detection time
* Impact
* Root cause
* Resolution
* Preventive actions

Post-incident reviews are mandatory for high-severity incidents.

---

# SLOs (Service Level Objectives)

Suggested initial objectives:

Availability

* 99.9%

API Success Rate

* 99.5%

Median Response Time

* Under 300 ms

Critical Queue Delay

* Under 60 seconds

These values should be reviewed as the platform evolves.

---

# Tooling

Recommended tooling:

Application

* Laravel Pulse
* Laravel Horizon
* Laravel Telescope (development)

Infrastructure

* Prometheus (future)
* Grafana (future)

Error Tracking

* Sentry or equivalent

Log Aggregation

* Centralized logging solution

---

# Release Verification

After every production deployment verify:

* Error rate
* Queue health
* API latency
* Database health
* Storage availability
* External integrations

---

# Definition of Observable

A feature is observable when:

* Important actions are logged.
* Metrics are collected.
* Errors are traceable.
* Health can be monitored.
* Failures can be diagnosed.

---

# Architecture Note — Every Request Must Be Traceable (ADR-017)

The base rule:

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

The goal: when a report comes in like "the Contribution never showed up," the full journey of that request can be followed end-to-end via its Request ID or Correlation ID — without guessing. See [ADR-017](../06-decisions/ADR-017-request-traceability.md).

---

# Related Documents

* Deployment Standards
* Security Standards
* Engineering Playbook
* ADRs
