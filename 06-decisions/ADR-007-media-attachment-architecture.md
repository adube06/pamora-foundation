# ADR-007 — Media Attachment Architecture

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Media

---

# Context

Media is often treated as a flat "gallery" attached loosely to an Occasion. But files in Pamora need to relate to many different entities — a receipt belongs to a Budget Item, a contract belongs to a Booking, a photo belongs to an Album — and a naive design either creates a new join table per entity type or lets files float without a clear owner ("orphan files"), both of which break auditability and retention.

Media is also strategically positioned as a **Digital Memory System**, not a gallery: after an Occasion ends, people return to look at photos, receipts, quotations, and schedules. That only works if every file has a durable, queryable relationship to the thing it documents.

---

# Decision

Every Media Asset must be owned by a specific entity, using a polymorphic attachment model (or the architectural equivalent):

```text
Occasion
│
├── Task
│     └── Attachments
│
├── Budget Item
│     └── Receipt
│
├── Booking
│     └── Contract
│
├── Announcement
│     └── Attachment
│
└── Gallery
      └── Photos
```

No orphan files are permitted (Business Rule BR-031).

---

# Consequences

* Any file can be associated with any entity without adding a new table each time a new attachable entity is introduced.
* Files are easy to find within their business context (e.g. "show me all documents attached to this Booking").
* Simplifies auditing and retention policy enforcement, since ownership is always explicit.
* Scales cleanly as new domains are added, without schema churn in the Media Domain.
* Requires consistent authorization checks at the attachment level — visibility (Business Rule-driven: Private / Committee Only / Occasion Members / Guests / Public) must be enforced per asset, not just per owning entity.

---

# Related Documents

* [Media PRD](../02-product/prd/07-media.md)
* [Business Rules](../02-product/05-business-rules.md) — BR-031, BR-032
* [Database Standards](../04-engineering/06-database-blueprint.md)
