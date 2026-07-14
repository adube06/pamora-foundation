# {METHOD} {/api/v1/resource}

**Domain:** {Owning Domain}

**Status:** Draft | Stable | Deprecated

---

# Purpose

What this endpoint does, in one sentence.

---

# Authentication

Required | Not Required

---

# Authorization

Which permission(s)/Occasion Membership capability is required (see [ADR-009](../06-decisions/ADR-009-identity-separate-from-membership.md) and [ADR-015](../06-decisions/ADR-015-default-deny.md)).

---

# Request

```text
{METHOD} /api/v1/{resource}
```

**Path Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| | | |

**Query Parameters:**

| Name | Type | Description |
| --- | --- | --- |
| | | |

**Body:**

```json
{}
```

---

# Response

**Success (2xx):**

```json
{
  "success": true,
  "data": {},
  "meta": {},
  "links": {}
}
```

**Error:**

```json
{
  "success": false,
  "error": {
    "code": "",
    "message": ""
  }
}
```

---

# Validation

List required fields, constraints, and business-rule-driven validation (reference BR-XXX where applicable).

---

# Permissions / Error Cases

| Status | Condition |
| --- | --- |
| 401 | Not authenticated |
| 403 | Authenticated but not authorized |
| 404 | Resource not found |
| 422 | Validation failed |

---

# Domain Events

Which events does this endpoint trigger?

---

# Related Documents

* [API Standards](../04-engineering/07-api-specification.md)
* Relevant Domain PRD
