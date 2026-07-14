# Occasion Domain PRD

**Version:** 1.0.0

**Status:** Approved

**Stability:** Mixed (see [Stability Within a Domain PRD](../01-prd.md#stability-within-a-domain-prd))

---

# 1. Purpose

The Occasion Domain is the core of the Pamora platform.

Every business capability exists to support an Occasion throughout its lifecycle.

An Occasion represents a real-world event that people organize together, such as a wedding, funeral, birthday, graduation, religious celebration, fundraiser, or corporate gathering.

Every workspace, participant, task, contribution, booking, announcement, and document ultimately belongs to one Occasion.

---

# 2. Business Goals

The Occasion Domain enables users to:

* Create an Occasion in minutes.
* Organize planning in one workspace.
* Coordinate participants.
* Track readiness.
* Preserve historical records.
* Reuse knowledge for future occasions.

Success is measured by successful completion of real-world occasions.

---

# 3. Scope

The Occasion Domain owns:

* Occasion
* Occasion Type
* Occasion Lifecycle
* Occasion Settings
* Occasion Visibility
* Occasion Templates (Future)
* Occasion Archive

It does **not** own:

* Tasks (Planning)
* Contributions (Finance)
* Vendor Bookings (Marketplace)
* Announcements (Communication)
* Photos (Media)

---

# 4. Core Entity

## Occasion

Represents one collaborative workspace.

### Required Attributes

* Unique Identifier
* Public Slug
* Title
* Occasion Type
* Description
* Primary Date
* Timezone
* Location
* Visibility
* Status
* Host
* Created Date
* Updated Date

---

# 5. Occasion Types (MVP)

Supported:

* Wedding
* Funeral
* Birthday

Future:

* Graduation
* Baby Shower
* Kitchen Party
* Religious Event
* Community Fundraiser
* Corporate Event
* Conference

The platform must support adding new Occasion Types without changing core business logic.

---

# 6. Occasion Lifecycle

Every Occasion progresses through defined states.

```text
Draft
   ↓
Planning
   ↓
Active
   ↓
Completed
   ↓
Archived
```

Alternative transitions:

```text
Draft
   ↓
Cancelled
```

Rules:

* Only valid transitions are permitted.
* Every transition creates an Activity Log.
* State changes may trigger notifications.

---

# 7. Functional Requirements

## FR-001 — Create Occasion

Priority: Critical

The system shall allow an authenticated user to create a new Occasion.

Acceptance Criteria:

* Required fields validated.
* Occasion created successfully.
* Host assigned automatically.
* Default settings applied.
* Activity recorded.

---

## FR-002 — Edit Occasion

Priority: High

The Host or authorized member may update Occasion information while the Occasion is not Archived.

---

## FR-003 — Archive Occasion

Priority: High

Completed Occasions may be archived.

Archived Occasions become read-only except for explicitly permitted operations.

---

## FR-004 — Cancel Occasion

Priority: Medium

Hosts may cancel an Occasion before completion.

Cancellation preserves historical records.

---

## FR-005 — Duplicate Occasion (Future)

The system may allow a completed Occasion to be copied as the starting point for another Occasion.

---

# 8. Visibility

Supported visibility levels:

* Private
* Invitation Only
* Public

Visibility affects:

* Searchability
* Invitation access
* Public pages
* Contribution pages

---

# 9. Permissions

## Host

Can:

* Edit details
* Invite members
* Change settings
* Archive
* Cancel
* Transfer ownership

---

## Committee Member

May perform delegated actions based on assigned permissions.

---

## Guest

Can only access information explicitly shared with them.

---

## Vendor

Can only access booking-related information relevant to their services.

---

# 10. Domain Events

The Occasion Domain emits events including:

* OccasionCreated
* OccasionUpdated
* OccasionPublished
* OccasionArchived
* OccasionCancelled
* OccasionCompleted
* OccasionOwnershipTransferred

Other domains subscribe to these events when needed.

---

# 11. Integrations

Planning Domain

* Creates default planning structure.

Finance Domain

* Initializes budget workspace.

Marketplace Domain

* Links vendor bookings.

Communication Domain

* Enables invitation workflows.

Media Domain

* Creates media library.

Insights Domain

* Starts readiness tracking.

---

# 12. Security

Only authorized users may:

* Edit
* Archive
* Cancel
* Transfer ownership

Sensitive actions require audit logging.

---

# 13. Reporting

Key metrics include:

* Total Occasions
* Active Occasions
* Completed Occasions
* Cancelled Occasions
* Average Planning Duration
* Repeat Hosts

---

# 14. Success Metrics

The domain succeeds when:

* Occasion creation is fast.
* Planning begins immediately.
* Collaboration is straightforward.
* Completion rate increases.
* Users return for future occasions.

---

# 15. Future Enhancements

Potential future capabilities:

* Occasion Templates
* AI Planning Assistant
* Multi-day Occasions
* Recurring Occasions
* Linked Occasions
* Cross-organization Occasions
* Smart Recommendations
* AI-generated Checklists

---

# Architecture Note — Occasion as Workspace

After reviewing the full architecture, the Occasion should not be treated as a "record" only.

It should be treated as a **Workspace**.

For example, opening a single Wedding should not show "details" alone. It should open into a workspace containing:

```text
Amina & John Wedding
────────────────────────
Overview
Planning
Committee
Guests
Invitations
Finance
Marketplace
Timeline
Media
Announcements
Activity
Settings
```

So in Flutter and Laravel:

```text
Occasion = Workspace
Workspace = Container for all business domains
```

This is an architecture decision that makes Pamora feel like a Notion for occasions, a Slack for committees, and an Airbnb for vendors — all within one workspace. See [ADR-001](../../06-decisions/ADR-001-occasion-as-workspace.md).

---

# Related Documents

* Domain Model
* Business Rules
* User Journeys
* Information Architecture
* Planning PRD
* Finance PRD
