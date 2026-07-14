# Pamora MVP Definition

**Version:** 1.0.0

**Status:** Approved

**Stability:** Controlled

---

# Purpose

This document defines the minimum viable product (MVP) for Pamora.

The MVP represents the smallest complete product capable of delivering real value to users while validating the core business assumptions.

Every feature must be classified as one of:

* MVP
* Post-MVP
* Future

Only MVP features are eligible for implementation in Version 1.0.

---

# Product Vision

Enable people to successfully organize important occasions through a collaborative digital workspace.

The MVP focuses on planning and coordination.

It intentionally excludes advanced automation and premium capabilities.

---

# Target Users

Primary:

* Occasion Hosts

Secondary:

* Committee Members

Supporting:

* Guests

Vendors are not a V1.0 persona. Marketplace and vendor capability are introduced in Release 1.1 (see [Roadmap](08-roadmap.md)).

---

# Success Criteria

The MVP is successful if users can:

* Create an Occasion.
* Invite committee members.
* Assign responsibilities.
* Plan work.
* Track a budget.
* Record contributions.
* Track expenses.
* Share invitations.
* Complete an Occasion.

---

# Included Domains

## Occasion

Included:

* Create Occasion
* Edit Occasion
* Occasion Dashboard
* Occasion Settings
* Occasion Lifecycle

Excluded:

* Templates
* Recurring Occasions
* Multi-day Occasions

---

## People

Included:

* Invitations
* Membership
* Responsibilities
* Basic permissions
* RSVP

Excluded:

* Teams
* Volunteer management
* Family relationships

---

## Planning

Included:

* Tasks
* Checklists
* Milestones
* Timeline
* Progress tracking

Excluded:

* AI planning
* Calendar synchronization
* Recurring tasks

---

## Finance

Included:

* Budget
* Budget Categories
* Contributions
* Expenses
* Financial Dashboard

Excluded:

* Payment gateway integration
* Automatic reconciliation
* Installments

---

## Marketplace

**Deferred to Release 1.1.** Not part of V1.0.

V1.0 ships with no Marketplace capability at all: no vendor registration, vendor profiles, vendor services, quotation requests, or booking workflow. See Release 1.1 in the [Roadmap](08-roadmap.md) for full scope.

---

## Communication

Included:

* Announcements
* Notifications
* Reminder rules
* Email delivery

Excluded:

* WhatsApp
* SMS
* Push notifications
* In-app chat

---

## Media

Included:

* Upload files
* Albums
* Documents
* Attachments

Excluded:

* AI tagging
* OCR
* Facial grouping

---

## Insights

Included:

* Readiness Score
* Financial Summary
* Task Progress
* Basic reports

Excluded:

* AI recommendations
* Predictive analytics
* Benchmarking

---

## Identity

Included:

* Registration
* Login
* Password reset
* Email verification
* Profile management

Excluded:

* Social login
* MFA
* Passkeys

---

# Mobile Application

Included:

* Home
* Occasion Workspace
* Planning
* Finance
* Guests
* Notifications
* Profile

Excluded:

* Offline mode
* Tablet optimization

---

# Web Application

Included:

* Public Occasion Page
* RSVP

Excluded:

* Vendor profiles (Release 1.1 — Marketplace is not part of V1.0)
* Public marketplace search optimization
* Organization portal

---

# Admin Portal

Included:

* User management
* Occasion management
* Reports
* Audit logs

Excluded:

* Vendor approval (Release 1.1 — Marketplace is not part of V1.0)
* CMS
* Advanced moderation
* Analytics dashboards

---

# Non-Functional Requirements

The MVP must support:

* Secure authentication
* Audit logging
* Responsive UI
* Localization readiness
* Basic accessibility
* Scalable architecture

---

# Explicitly Out of Scope

The following are **not** part of Version 1.0:

* AI Assistant
* Organization Workspace
* Public APIs
* Payment processing
* WhatsApp integration
* Mobile Push Notifications
* Offline synchronization
* Advanced analytics
* Workflow automation
* Marketplace subscriptions
* Multi-language content generation

---

# Release Gate

Version 1.0 may be released only if:

* All critical business flows are complete.
* No critical defects remain.
* Security review is complete.
* Core user journeys pass acceptance testing.
* Production monitoring is operational.

---

# Exit Criteria

The MVP is considered validated when:

* Users successfully organize real Occasions.
* Planning completion rate improves.
* Users return for additional Occasions.
* Feedback confirms product-market fit assumptions.

---

# Release Slicing (Adopted)

The Included Domains above are further sliced into releases, ahead of coding. This is the authoritative V1.0 scope — the "Marketplace" and "Vendor" exclusions above exist because of this slicing decision.

## V1.0 (Core)

* Occasion Workspace
* Committee
* Guests & RSVP
* Planning
* Budget
* Contributions
* Expenses
* Documents
* Announcements
* Basic Insights
* Admin Panel

## V1.1

* Vendor Marketplace
* Quotations
* Bookings
* Reviews

## V1.2

* Mobile Money
* Email automation
* Calendar integration

## V2.0

* AI Assistant
* Smart recommendations
* Organization Workspace
* Public APIs
* Advanced analytics

By slicing this way:

* Backend stays simpler.
* Flutter stays lighter.
* Testing stays simpler.
* The product ships earlier and gathers real user feedback before harder areas like Marketplace and AI are built.

---

# Related Documents

* Product Scope
* PRD
* User Journeys
* Release Plan
* Engineering Playbook
