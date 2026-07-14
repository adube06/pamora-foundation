# People Domain PRD

**Version:** 1.0.0

**Status:** Approved

**Stability:** Mixed (see [Stability Within a Domain PRD](../01-prd.md#stability-within-a-domain-prd))

---

# 1. Purpose

The People Domain manages every person participating in an Occasion.

It defines how users join an Occasion, what responsibilities they have, and what information they can access.

This domain is responsible for participation, not authentication.

Authentication belongs to the Identity Domain.

---

# 2. Business Goals

Enable organizers to:

* Invite participants.
* Assign responsibilities.
* Control permissions.
* Track attendance.
* Coordinate collaboration.

The objective is to make teamwork around an Occasion simple and transparent.

---

# 3. Core Concepts

The People Domain is built around **Occasion Membership**.

A User becomes a participant only after joining an Occasion.

Membership defines the user's permissions and responsibilities within that specific Occasion.

The same User may have different roles in different Occasions.

---

# 4. Core Entities

## OccasionMember

Represents a User participating in an Occasion.

Owns:

* Membership Status
* Permissions
* Responsibilities
* Invitation Status
* RSVP Status
* Attendance Status

---

## Invitation

Represents an invitation sent to a participant.

States:

* Pending
* Accepted
* Declined
* Expired
* Revoked

---

## Responsibility

Represents duties assigned within an Occasion.

Examples:

* Chairperson
* Treasurer
* Secretary
* Catering Lead
* Logistics Lead
* Decoration Lead
* Transport Coordinator

A participant may hold multiple responsibilities.

---

# 5. Functional Requirements

## FR-001 — Invite Participant

The Host or authorized member shall invite a User to an Occasion.

Acceptance Criteria:

* Invitation created.
* Invitation delivered.
* Invitation recorded.
* Audit entry generated.

---

## FR-002 — Accept Invitation

The invited User may accept an invitation.

Acceptance Criteria:

* Membership created.
* Permissions assigned.
* Activity recorded.

---

## FR-003 — Decline Invitation

Users may decline invitations without affecting the Occasion.

---

## FR-004 — Assign Responsibilities

Authorized users may assign one or more responsibilities to an Occasion Member.

---

## FR-005 — Remove Participant

Authorized users may remove members before the Occasion is completed.

Historical records remain intact.

---

## FR-006 — Transfer Ownership

The Host may transfer ownership of the Occasion to another eligible member.

Ownership transfer must be recorded in the audit log.

---

# 6. Membership Lifecycle

```text
Invited
    │
    ▼
Accepted
    │
    ▼
Active
    │
    ▼
Completed
```

Alternative paths:

```text
Invited
    │
    ├── Declined
    ├── Expired
    └── Revoked
```

---

# 7. Permissions

Permissions should be assigned through capabilities rather than hard-coded roles.

The examples below are illustrative umbrella categories, not enforceable permission strings. The actual, canonical permission catalog — the exact strings checked in code — lives in the [Permission Catalog](../09-permission-catalog.md) and is organized per-domain (`finance.edit_budget`, `finance.record_contribution`, etc.), not as broad umbrellas like "Manage Finance."

Illustrative categories:

* Manage Occasion
* Manage Planning
* Manage Finance
* Invite Members
* Manage Vendors
* Publish Announcements
* View Reports

Responsibilities describe **what someone does**.

Permissions describe **what someone may do**.

These concepts must remain separate.

---

# 8. RSVP

Guests may respond with:

* Attending
* Not Attending
* Maybe

Optional fields:

* Number of attendees
* Message
* Dietary requirements (Future)

---

# 9. Domain Events

This domain emits events such as:

* InvitationSent
* InvitationAccepted
* InvitationDeclined
* MemberJoined
* MemberRemoved
* ResponsibilityAssigned
* OwnershipTransferred

---

# 10. Security

Only authorized members may:

* Invite participants.
* Assign permissions.
* Remove participants.
* Transfer ownership.

Every permission change must be logged.

---

# 11. Reporting

Key metrics include:

* Total Participants
* Accepted Invitations
* Declined Invitations
* RSVP Rate
* Committee Size
* Participation Rate

---

# 12. Future Enhancements

Potential future capabilities:

* Teams within an Occasion
* Delegation of responsibilities
* Volunteer management
* Family relationships
* Contact groups
* Smart invitation suggestions

---

# Architecture Note — Unified Membership Model

Before implementation begins, one architectural correction should be made early.

Do not build tables like:

```text
hosts
guests
committee_members
```

This looks simple today, but after roughly 12 months it becomes a problem.

Instead, the foundation of the system should be:

```text
User
    │
    ▼
OccasionMember
    │
    ├── permissions
    ├── responsibilities
    ├── invitation_status
    ├── attendance_status
    └── metadata
```

Why? Because one person can be:

* Host on their own Wedding.
* Treasurer on a friend's wedding.
* Guest on a Birthday.
* Vendor on another Event.

So the User does not change. What changes is their membership within an Occasion.

This is the same architecture used by large-scale systems such as Slack, GitHub Organizations, and Notion Workspaces. See [ADR-002](../../06-decisions/ADR-002-unified-occasion-member-model.md).

---

# Related Documents

* Occasion PRD
* Business Rules
* User Journeys
* Communication PRD
* Identity PRD
