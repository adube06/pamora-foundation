# ADR-006 — Event-Driven Communication

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Communication, all domains (as event producers)

---

# Context

If business domains call notification/email/SMS code directly (e.g. `TaskService` calling `Mail::send()` inline), the Communication Domain's responsibilities — deciding who to notify, through which channel, using which template, at what time — become scattered across every domain. Adding a new channel (WhatsApp, Push) would then require touching every domain that sends a notification.

---

# Decision

Domains never call communication/delivery code directly. Instead, they publish Domain Events, which the Communication Domain consumes:

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

Example triggering events: `TaskCompleted`, `ContributionReceived`, `BookingConfirmed`, `InvitationAccepted`.

The Communication Domain owns the decision of recipient, channel, template, and timing — not the originating domain.

---

# Consequences

* Business logic stays fully decoupled from notification/delivery code, consistent with the Engineering Playbook's Event Rules and "Things We Do Not Do" (no direct integration calls from business domains).
* Adding WhatsApp, Push Notifications, or a new email provider touches only the Communication Domain and the Integrations Domain — not Planning, Finance, or Marketplace.
* The system becomes easier to test: domain logic tests assert an event was emitted; Communication tests assert the event produces the right notification.
* Requires an event bus / listener infrastructure to be part of the Foundation layer from day one, not bolted on later.

---

# Related Documents

* [Communication PRD](../02-product/prd/06-communication.md)
* [Integrations PRD](../02-product/prd/10-integrations.md)
* [Engineering Playbook](../04-engineering/02-engineering-playbook.md) — Event Rules
