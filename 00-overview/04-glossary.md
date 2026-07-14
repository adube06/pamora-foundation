# Glossary

**Version:** 1.0.0

**Status:** Approved

**Stability:** Frozen

---

# Purpose

This glossary defines the official business language of Pamora.

Every person working on Pamora—including product managers, designers, engineers, QA, AI assistants, and business stakeholders—must use these terms consistently.

This document serves as the **Ubiquitous Language** for the platform.

If a term is defined here, it should be used consistently across:

* Documentation
* User Interface
* Database
* APIs
* Source Code
* Product Discussions

---

# Core Concepts

## Occasion

The primary business entity of the platform.

An Occasion is a collaborative workspace created to plan, coordinate, execute, and preserve an important event or gathering.

Examples include:

* Wedding
* Funeral
* Birthday
* Graduation
* Religious Celebration
* Conference
* Community Fundraiser
* Corporate Event

Every major feature in Pamora exists in relation to an Occasion.

---

## Occasion Host

The person who creates an Occasion.

The Host is responsible for the overall ownership of the Occasion.

A Host may delegate responsibilities to other people.

---

## Committee

A group of people responsible for helping organize an Occasion.

Committee members may receive different permissions depending on their responsibilities.

Examples:

* Chairperson
* Treasurer
* Secretary
* Logistics Lead
* Food Coordinator

A committee is not a permanent organization.

It exists within the context of an Occasion.

---

## Guest

A person invited to participate in an Occasion.

Guests may:

* View event information
* RSVP
* Receive updates
* Contribute financially (if enabled)
* Leave messages
* Access shared resources

Guests are participants, not administrators.

---

## Invitation

A digital invitation sent to a Guest.

An invitation may contain:

* Occasion details
* Venue
* Schedule
* Dress code
* Directions
* RSVP request
* Contribution information
* QR Code
* Shareable link

---

## RSVP

A guest's response indicating attendance.

Possible statuses include:

* Pending
* Attending
* Not Attending
* Maybe

---

# Financial Terms

## Contribution

A financial commitment made toward an Occasion.

A Contribution may represent:

* Cash support
* Mobile Money transfer
* Card payment
* Bank transfer
* Other approved payment methods

A Contribution progresses through defined business states.

---

## Pledge

A promise to contribute money in the future.

A pledge does not necessarily mean that payment has been received.

A pledge may later become a confirmed contribution.

---

## Budget

The planned financial allocation for an Occasion.

Budgets define expected income and expected expenses.

---

## Expense

Money spent during the planning or execution of an Occasion.

Expenses should be categorized and traceable.

---

# Marketplace

## Vendor

A business or individual offering products or services through Pamora.

Examples include:

* Photographer
* Caterer
* Decorator
* DJ
* Master of Ceremony
* Tent Provider
* Car Rental
* Makeup Artist

One user account may operate as a Vendor while also participating in other occasions.

---

## Service

A non-inventory offering provided by a Vendor.

Examples:

* DJ Performance
* Photography
* Catering
* MC Services

Services are booked based on availability.

---

## Rental Item

A physical item offered for temporary use.

Examples:

* Chairs
* Tables
* Tents
* Sound Systems
* Decorations

Rental Items are inventory-based and require stock management.

---

## Booking

A confirmed request for a Vendor's Service or Rental Item.

A Booking has a lifecycle and may move through states such as:

* Pending
* Accepted
* Rejected
* In Progress
* Completed
* Cancelled

---

# Planning

## Task

A unit of work required to complete an Occasion.

Tasks may be assigned to individuals or committees.

---

## Timeline

The chronological schedule of important activities within an Occasion.

Examples include:

* Planning meetings
* Payment deadlines
* Vendor arrivals
* Ceremony start time

---

## Milestone

A significant checkpoint in the Occasion lifecycle.

Examples:

* Venue Confirmed
* Invitations Sent
* Catering Finalized
* Budget Approved

---

# Communication

## Announcement

A message broadcast to participants of an Occasion.

Announcements may be targeted to:

* All guests
* Committee members
* Vendors
* Specific groups

---

## Notification

A system-generated message informing users about activities requiring attention.

Notifications should be timely and actionable.

---

# Platform Concepts

## Workspace

The digital environment associated with an Occasion.

A Workspace contains all planning activities, participants, finances, tasks, documents, and communications.

---

## Health Score

A calculated indicator representing the overall readiness and health of an Occasion.

It may consider:

* Budget completion
* Task completion
* RSVP progress
* Vendor confirmations
* Contribution status
* Timeline risks

The Health Score helps organizers identify areas needing attention.

---

## Activity Log

A chronological record of important actions performed within an Occasion.

Examples include:

* Guest invited
* Budget updated
* Vendor booked
* Contribution confirmed

The Activity Log supports transparency and auditing.

---

# Technical Concepts

## Domain

A major business area of the platform.

Examples:

* Occasion
* Finance
* Marketplace
* Planning
* Communication

Each domain owns its own business rules and data.

---

## Aggregate

A group of related business entities treated as a single consistency boundary.

Pamora follows Domain-Driven Design principles where appropriate.

The Occasion is expected to be one of the primary aggregates.

---

## Business Rule

A constraint or policy governing system behavior.

Business Rules are defined by product requirements and must not be bypassed in implementation.

---

# Terminology Rules

The following replacements should be preferred throughout the project:

| Avoid    | Prefer                                                  |
| -------- | ------------------------------------------------------- |
| Event    | Occasion                                                |
| Customer | User (or specific role such as Host or Vendor)          |
| Admin    | Administrator                                           |
| Order    | Booking (where applicable)                              |
| Money    | Contribution, Budget, or Expense (depending on context) |

Terminology should always reflect the business meaning rather than generic software language.

---

# Related Documents

* AI Master Context
* Vision
* Mission
* Product Philosophy
* Domain Model
* Business Rules
* Product Requirements Document
