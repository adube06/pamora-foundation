# Domain Model

**Version:** 1.0.0

**Status:** Approved

**Stability:** Frozen

---

# Purpose

This document defines the major business domains of Pamora.

A Domain is a business capability with clear responsibilities, business rules, and ownership.

Pamora follows a **Domain-Driven Design (DDD)** approach.

Business domains should remain stable even if the underlying technology changes.

---

# Domain Overview

Pamora consists of 9 **Core Business Domains**, plus one **Supporting Technical Domain**:

## Core Business Domains

1. Identity
2. Occasion
3. People
4. Planning
5. Finance
6. Marketplace
7. Communication
8. Media
9. Insights

## Supporting Technical Domain

* **Integrations** — see the dedicated section below. It is deliberately excluded from the numbered Core Business Domain list above, because it owns no business data and enforces no business rule.

Each domain owns its own business logic and data.

No domain should directly manipulate another domain's internal state.

---

# 1. Identity Domain

## Responsibility

Manage identity, authentication, authorization, and user profiles.

---

## Owns

* User
* Profile
* Authentication
* Session
* Device
* Verification
* Preferences

---

## Responsibilities

* Registration
* Login
* Password management
* Identity verification
* Notification preferences
* Security settings

---

## Does NOT Own

* Guests
* Vendors
* Occasions
* Bookings
* Contributions

These belong to their respective domains.

---

# 2. Occasion Domain

## Responsibility

The central domain of the platform.

Every other domain interacts with an Occasion.

---

## Owns

* Occasion
* Occasion Type
* Occasion Status
* Occasion Settings
* Occasion Lifecycle

---

## Responsibilities

* Create Occasion
* Update Occasion
* Archive Occasion
* Lifecycle transitions
* Ownership
* Workspace creation

---

## Core Rule

Everything in Pamora exists because of an Occasion.

---

# 3. People Domain

## Responsibility

Manage everyone participating in an Occasion.

---

## Owns

* Host
* Committee Member
* Guest
* Invitation
* RSVP
* Participant Roles

---

## Responsibilities

* Invitations
* Guest management
* Committee management
* Participant permissions
* Attendance

---

## Important

A User may participate in many Occasions.

A User's responsibilities depend on the Occasion context.

---

# 4. Planning Domain

## Responsibility

Coordinate execution of the Occasion.

---

## Owns

* Task
* Checklist
* Timeline
* Milestone
* Calendar Event

---

## Responsibilities

* Task assignment
* Progress tracking
* Deadline management
* Planning workflows

---

# 5. Finance Domain

## Responsibility

Manage financial activities related to an Occasion.

---

## Owns

* Budget
* Budget Category
* Contribution
* Pledge
* Expense
* Financial Summary

---

## Responsibilities

* Budget tracking
* Contribution management
* Expense recording
* Financial reporting

---

## Payment Processing

Payment gateways integrate with this domain but do not define it.

---

# 6. Marketplace Domain

## Responsibility

Manage Vendor discovery and bookings.

---

## Owns

* Vendor
* Vendor Profile
* Service
* Rental Item
* Booking
* Availability
* Review

---

## Responsibilities

* Vendor onboarding
* Booking lifecycle
* Availability
* Pricing
* Reviews

---

# 7. Communication Domain

## Responsibility

Deliver information to participants.

---

## Owns

* Announcement
* Notification
* Reminder
* Message Template

---

## Responsibilities

* Broadcast communication
* Event reminders
* Push notifications
* Email notifications
* SMS integration

---

# 8. Media Domain

## Responsibility

Manage digital assets.

---

## Owns

* Photo
* Video
* Attachment
* Invitation Asset
* Document

---

## Responsibilities

* Upload
* Organization
* Access control
* Preservation

---

# 9. Insights Domain

## Responsibility

Generate analytics and decision support.

---

## Owns

* Dashboard
* Metrics
* Reports
* Readiness Score
* Recommendations

---

## Responsibilities

* Analytics
* Progress indicators
* Financial summaries
* Operational insights

This domain consumes data from other domains but should not modify them.

---

# 10. Integrations (Supporting Technical Domain)

## Classification

**Supporting Technical Domain — not a Core Business Domain.**

In DDD terms, Integrations is a supporting/generic subdomain: it exists to serve the 9 Core Business Domains, not to model a business capability of its own. This is why it is numbered separately here rather than counted among the 9, and why it does not appear as a node in the Domain Relationships diagram below — every Core Business Domain may call into it, but it does not sit *in* the domain dependency chain.

## Responsibility

Provide a provider-independent interface for external systems (payment gateways, SMS/email/WhatsApp, maps, calendar, object storage, authentication providers), so that Core Business Domains never couple directly to a specific vendor's API.

## Owns

* Provider Configuration
* API Connectors
* Webhook Processing
* Retry Policies
* External Credentials

## Does NOT Own

Business data or business rules of any kind. It has no aggregate root and is not eligible to become one — a domain that owned business data would need to be reclassified as a Core Business Domain, which would itself require a constitutional discussion (see the Constitution, Article V).

## Relationship to Core Business Domains

Every Core Business Domain that needs an external provider depends on Integrations directly (Communication for delivery, Finance for payment gateways, Marketplace and Occasion for maps, Media for storage, Identity for external auth providers). See the [Integrations PRD](../02-product/prd/10-integrations.md) for the full list.

---

# Domain Relationships

```text
Identity
     │
     ▼
 Occasion
 ├──────────────┐
 ▼              ▼
People      Planning
 │              │
 ├──────┐       │
 ▼      ▼       ▼
Finance Marketplace
       │
       ▼
Communication
       │
       ▼
Media
       │
       ▼
Insights
```

---

# Cross-Domain Rules

The following principles apply across all domains:

* Domains communicate through well-defined interfaces.
* Business rules remain within the owning domain.
* Avoid circular dependencies.
* Shared concepts should be referenced, not duplicated.
* Every domain should be independently testable.

---

# Aggregate Roots (Initial)

The primary aggregates are expected to be:

* Occasion
* Vendor
* Booking
* Budget
* Contribution

Additional aggregates may be introduced as the platform evolves.

---

# Evolution Strategy

New domains should be introduced only when:

* Existing domains become overloaded.
* Business complexity justifies separation.
* Clear ownership can be established.

Avoid creating domains based solely on technical convenience.

---

# Related Documents

* Product Principles
* Product Scope
* Business Rules
* Information Architecture
* Engineering Playbook
* PRD
