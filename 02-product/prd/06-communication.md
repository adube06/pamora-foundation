# Communication Domain PRD

**Version:** 1.0.0

**Status:** Approved

**Stability:** Frozen (see [Stability Within a Domain PRD](../01-prd.md#stability-within-a-domain-prd))

---

# 1. Purpose

The Communication Domain manages the exchange of information within and around an Occasion.

It ensures that Hosts, Committee Members, Guests, and Vendors receive timely, relevant, and traceable communications.

The domain centralizes announcements, notifications, invitations, reminders, and messaging triggers.

Many people treat this domain as "notifications" only — for Pamora it is the communication hub of the entire Occasion.

---

# 2. Business Goals

Enable users to:

* Keep everyone informed.
* Reduce missed updates.
* Improve planning coordination.
* Automate repetitive communications.
* Maintain a communication history.

---

# 3. Scope

The Communication Domain owns:

* Announcements
* Notifications
* Message Templates
* Reminder Rules
* Delivery Logs
* Communication Preferences

It does **not** own:

* Authentication
* Media Storage
* Vendor Profiles
* Budget Records

---

# 4. Core Entities

## Announcement

Represents an official communication within an Occasion.

Examples:

* Meeting reminder
* Venue update
* Schedule change
* Emergency notice

Attributes:

* Title
* Message
* Audience
* Publish Time
* Author
* Status

---

## Notification

Represents a system-generated event delivered to users.

Examples:

* Task assigned
* Contribution received
* Vendor confirmed
* RSVP submitted
* Booking updated

Notifications are generated automatically from Domain Events.

---

## Message Template

Reusable templates for common communications.

Examples:

* Invitation
* Reminder
* Thank You
* Booking Confirmation
* Contribution Receipt

Templates support localization.

---

## Reminder Rule

Defines when reminders should be sent.

Examples:

* 7 days before the Occasion
* 24 hours before a Task deadline
* 2 hours before a meeting

---

## Delivery Log

Tracks communication delivery.

Fields include:

* Channel
* Recipient
* Delivery Status
* Timestamp
* Failure Reason (if any)

---

# 5. Delivery Channels

Supported channels:

* In-App Notifications
* Email
* SMS
* WhatsApp (Future)
* Push Notifications (Future)

Each user may define preferred delivery channels.

---

# 6. Functional Requirements

## FR-001 — Publish Announcement

Authorized members may publish an Announcement.

Acceptance Criteria:

* Announcement saved.
* Audience selected.
* Delivery initiated.
* Activity logged.

---

## FR-002 — Generate Notification

The system shall generate Notifications in response to Domain Events.

---

## FR-003 — Schedule Reminder

Users may configure Reminder Rules for supported activities.

---

## FR-004 — View Communication History

Users may review historical Announcements and Notifications they are authorized to access.

---

## FR-005 — Manage Preferences

Users may enable or disable supported notification channels where applicable.

---

# 7. Domain Events

The Communication Domain consumes events from other domains and may emit:

* AnnouncementPublished
* ReminderTriggered
* NotificationDelivered
* NotificationFailed
* PreferenceUpdated

---

# 8. Integrations

Occasion Domain

* Occasion lifecycle updates

People Domain

* Invitations
* Membership changes

Planning Domain

* Task reminders
* Milestone alerts

Finance Domain

* Contribution confirmations
* Budget alerts

Marketplace Domain

* Booking updates
* Quotation responses

---

# 9. Security

Only authorized users may:

* Publish Announcements.
* Schedule Reminders.
* View restricted communications.

Communication history must respect Occasion permissions.

---

# 10. Reporting

Metrics include:

* Notifications Sent
* Delivery Success Rate
* Open Rate (where supported)
* Reminder Completion Impact
* Failed Deliveries

---

# 11. Success Metrics

The Communication Domain succeeds when:

* Users receive timely updates.
* Critical information reaches the intended audience.
* Delivery failures are traceable.
* Communication overload is minimized.

---

# 12. Future Enhancements

Potential capabilities:

* Two-way messaging
* Group discussions
* AI-generated announcements
* Smart reminder timing
* Translation support
* Voice announcements
* Broadcast channels

---

# Architecture Note — Event-Driven Communication (ADR-006)

Communication must not be called directly from business logic.

Instead:

```text
TaskCompleted
        │
        ▼
Domain Event
        │
        ▼
Communication Domain
        │
        ▼
Notification
        │
        ▼
Email / SMS / In-App
```

Examples of triggering events:

* TaskCompleted
* ContributionReceived
* BookingConfirmed
* InvitationAccepted

All of these emit Domain Events, and the Communication Domain decides:

* Who should be notified.
* Through which channel.
* Using which template.
* At what time.

Benefits:

* Business logic stays decoupled from notification code.
* Adding WhatsApp, Push Notifications, or a new Email provider will not change other domains.
* The system stays testable and extensible.

See [ADR-006](../../06-decisions/ADR-006-event-driven-communication.md).

---

# Related Documents

* Occasion PRD
* People PRD
* Planning PRD
* Business Rules
* User Journeys
