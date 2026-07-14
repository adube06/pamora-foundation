# Media Domain PRD

**Version:** 1.0.0

**Status:** Approved

**Stability:** Mixed (see [Stability Within a Domain PRD](../01-prd.md#stability-within-a-domain-prd))

---

# 1. Purpose

The Media Domain manages all digital assets associated with an Occasion.

It provides secure storage, organization, retrieval, and preservation of photos, videos, documents, and other files throughout the Occasion lifecycle.

The objective is to preserve the complete digital memory of every Occasion.

Media should not be treated as a "gallery." It should be treated as a **Digital Memory System**. After an Occasion ends, people return to look at photos, videos, documents, quotations, receipts, schedules, and memories. That is Pamora's long-term value.

---

# 2. Business Goals

Enable users to:

* Store media securely.
* Organize assets by context.
* Share approved media.
* Preserve historical records.
* Retrieve files efficiently.

---

# 3. Scope

The Media Domain owns:

* Photos
* Videos
* Documents
* Albums
* File Metadata
* Media Permissions
* Storage References

It does **not** own:

* Communication
* User Authentication
* Vendor Profiles
* Financial Records

---

# 4. Core Entities

## Media Asset

Represents a single uploaded file.

Supported types:

* Image
* Video
* PDF
* Document
* Audio (Future)

Attributes:

* File Name
* File Type
* Size
* Storage Location
* Uploaded By
* Upload Date
* Related Entity
* Visibility

---

## Album

Groups related Media Assets.

Examples:

* Engagement
* Ceremony
* Reception
* Decorations
* Vendor Deliverables
* Financial Documents

---

## Document

Represents important files attached to an Occasion.

Examples:

* Quotations
* Contracts
* Receipts
* Guest Lists
* Schedules
* Permits

Documents should support version tracking where applicable.

---

# 5. Functional Requirements

## FR-001 — Upload Media

Authorized users may upload Media Assets.

Acceptance Criteria:

* File validated.
* Metadata stored.
* Activity logged.
* Ownership assigned.

---

## FR-002 — Organize Albums

Users may create Albums and move Media Assets between them.

---

## FR-003 — Attach Files

Media Assets may be linked to:

* Tasks
* Budget Items
* Vendor Bookings
* Announcements
* Occasion Records

---

## FR-004 — Download Media

Authorized users may download original files.

Access must respect Occasion permissions.

---

## FR-005 — Archive Media

Archived Occasions retain Media Assets according to the retention policy.

---

# 6. Visibility

Supported visibility levels:

* Private
* Committee Only
* Occasion Members
* Guests
* Public

Visibility applies per Media Asset.

---

# 7. Domain Events

The Media Domain emits:

* MediaUploaded
* MediaUpdated
* MediaDeleted
* AlbumCreated
* AlbumArchived
* DocumentAttached

---

# 8. Integrations

Occasion Domain

* Occasion gallery

Planning Domain

* Task attachments

Finance Domain

* Receipts
* Budget documents

Marketplace Domain

* Vendor portfolios
* Deliverables

Communication Domain

* Shared attachments

Insights Domain

* Storage analytics

---

# 9. Security

Only authorized users may:

* Upload
* Edit metadata
* Delete
* Download
* Share

Deleted files should follow the platform retention policy.

---

# 10. Reporting

Metrics include:

* Total Files
* Storage Usage
* Upload Activity
* Most Viewed Albums
* Document Count
* Media Growth Over Time

---

# 11. Success Metrics

The Media Domain succeeds when:

* Files are easy to upload.
* Assets are easy to locate.
* Permissions are enforced consistently.
* Historical media remains accessible.

---

# 12. Future Enhancements

Potential capabilities:

* AI image tagging
* Facial grouping (subject to privacy controls)
* OCR for documents
* Video highlights
* Duplicate detection
* Cloud backup
* Offline synchronization
* Shared family archives

---

# Architecture Note — Polymorphic Attachment Model (ADR-007)

Files must not be stored "floating" without a relationship.

Every Media Asset must be owned by a specific entity.

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

Therefore, Media should use a polymorphic attachment model (or the architectural equivalent), so that any file can be associated with any entity without adding new tables each time.

Benefits:

* No orphan files.
* Files are easy to find within context.
* Simplifies auditing and retention.
* Scales cleanly as more domains are added.

See [ADR-007](../../06-decisions/ADR-007-media-attachment-architecture.md).

---

# Related Documents

* Occasion PRD
* Communication PRD
* Finance PRD
* Business Rules
* Information Architecture
