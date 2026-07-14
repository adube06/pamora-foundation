# Pamora API Standards

**Version:** 1.0.0

**Status:** Mandatory

**Stability:** Frozen

---

# Purpose

This document defines the standards for all APIs exposed by Pamora.

The objectives are:

* Consistency
* Predictability
* Security
* Versioning
* Long-term maintainability

Every API must follow these standards.

---

# API Style

Pamora exposes REST APIs.

Base URL:

```text
/api/v1
```

Future breaking changes require a new API version.

---

# Resource Naming

Use plural nouns.

Examples:

```text
GET    /occasions
POST   /occasions

GET    /tasks
POST   /tasks

GET    /vendors
POST   /vendors
```

Nested resources should reflect ownership.

Example:

```text
GET /occasions/{occasion}/tasks
```

Avoid deep nesting beyond two levels.

---

# HTTP Methods

GET

* Read data

POST

* Create resources

PUT

* Replace resources

PATCH

* Partial updates

DELETE

* Remove resources

Methods must not be overloaded.

---

# Response Format

Every successful response follows:

```json
{
  "success": true,
  "data": {},
  "meta": {},
  "links": {}
}
```

---

Errors follow:

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Validation failed."
  }
}
```

Never expose stack traces.

---

# Status Codes

200 OK

201 Created

202 Accepted

204 No Content

400 Bad Request

401 Unauthorized

403 Forbidden

404 Not Found

409 Conflict

422 Validation Error

429 Too Many Requests

500 Internal Server Error

Use the most specific code available.

---

# Validation

Validate at request boundaries.

Return validation errors in a consistent structure.

Example:

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "fields": {
      "title": [
        "Title is required."
      ]
    }
  }
}
```

---

# Pagination

Use cursor pagination for large collections.

Response includes:

```json
{
  "data": [],
  "meta": {
    "next_cursor": "...",
    "previous_cursor": "..."
  }
}
```

Avoid offset pagination for frequently changing datasets.

---

# Filtering

Standard query parameters:

```text
?status=active

?type=wedding

?priority=high
```

Multiple filters may be combined.

---

# Sorting

Example:

```text
?sort=created_at

?sort=-created_at

?sort=name
```

A leading "-" indicates descending order.

---

# Searching

Standard parameter:

```text
?q=photographer
```

Search behavior should be documented per resource.

---

# Includes

Support related resources where appropriate.

Example:

```text
GET /occasions/1?include=tasks,members
```

Avoid unnecessary database queries.

---

# Field Selection

Clients may request subsets.

Example:

```text
GET /vendors?fields=id,name,rating
```

---

# Authentication

Use token-based authentication.

All protected endpoints require authentication.

Public endpoints must be explicitly documented.

---

# Authorization

Authentication identifies the user.

Authorization determines permissions.

Every protected action must pass authorization checks.

---

# Idempotency

Operations that may be retried (such as payment initiation) should support idempotency keys where appropriate.

---

# Rate Limiting

Protect all public endpoints.

Rate limits should be configurable.

Responses should indicate when limits are exceeded.

---

# File Uploads

Uploads must:

* Validate type
* Validate size
* Scan where applicable
* Return metadata only

Large uploads should support asynchronous processing.

---

# Date & Time

Use ISO 8601.

Store timestamps in UTC.

Convert to the user's preferred timezone only when presenting data.

---

# API Versioning

Breaking changes require:

```text
/api/v2
```

Non-breaking enhancements remain within the current version.

---

# Documentation

Every endpoint must document:

* Purpose
* Authentication
* Request
* Response
* Validation
* Permissions
* Error cases

OpenAPI generation is recommended.

---

# Deprecation

Deprecated endpoints must:

* Be documented.
* Provide migration guidance.
* Remain available for a defined deprecation period.

---

# Observability

Every request should include:

* Request ID
* Correlation ID
* Duration
* Status Code

Sensitive information must never appear in logs.

---

# Definition of a Production-Ready API

An endpoint is production-ready when it has:

* Validation
* Authorization
* Tests
* Documentation
* Logging
* Monitoring
* Consistent responses
* Performance review

---

# Architecture Note — APIs Are Contracts (ADR-012)

In Pamora:

* React does not own the API.
* Flutter does not own the API.
* The backend does not own the UI.

The API is the contract that connects all of them.

Any change that breaks the contract requires:

* A new API version, or
* A backward-compatibility plan.

See [ADR-012](../06-decisions/ADR-012-apis-are-contracts.md).

---

# Related Documents

* Engineering Playbook
* Security Standards
* Database Standards
* Testing Strategy
