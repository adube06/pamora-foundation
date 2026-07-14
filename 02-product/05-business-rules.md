# Business Rules

**Version:** 1.0.0

**Status:** Approved

**Stability:** Frozen

---

# Purpose

This document defines the official business rules governing the Pamora platform.

Business Rules describe **how the platform must behave** regardless of implementation details.

These rules are technology-independent and must be respected across:

* Mobile Application
* Web Application
* APIs
* Admin Panel
* Background Jobs
* Integrations

When implementation conflicts with a Business Rule, the Business Rule takes precedence.

---

# Rule Format

Each rule has:

* Unique ID
* Domain
* Priority
* Description

Priority levels:

* Critical
* High
* Medium
* Low

---

# Identity Domain

### BR-001

**Priority:** Critical

A User Account must be unique.

Duplicate accounts using the same verified identifier are not permitted.

---

### BR-002

A User may participate in multiple Occasions simultaneously.

---

### BR-003

A User may own multiple Occasions.

---

### BR-004

Authentication is required for all private workspace operations.

---

# Occasion Domain

### BR-005

Every Occasion must have exactly one Host.

Ownership may be transferred but cannot be shared simultaneously in the initial release.

---

### BR-006

Every Occasion belongs to exactly one Occasion Type.

Examples:

* Wedding
* Funeral
* Birthday

---

### BR-007

Every Occasion must have one lifecycle status.

Example statuses:

* Draft
* Planning
* Active
* Completed
* Archived
* Cancelled

---

### BR-008

Completed Occasions become read-only except where explicitly permitted.

---

### BR-009

Archived Occasions cannot receive new activities.

---

# People Domain

### BR-010

A Participant belongs to an Occasion.

Participation has no meaning outside an Occasion.

---

### BR-011

A Participant may hold multiple responsibilities within the same Occasion.

Example:

A person may be both Treasurer and Committee Member.

---

### BR-012

Invitation links may expire.

---

### BR-013

A Guest may respond to an invitation only once unless the Host reopens RSVP.

---

# Planning Domain

### BR-014

Every Task belongs to one Occasion.

---

### BR-015

A Task may have zero or one assignee.

Future releases may support multiple assignees.

---

### BR-016

Completed Tasks cannot be modified except by authorized users.

---

### BR-017

Milestones are achieved automatically when all required conditions are satisfied.

---

# Finance Domain

### BR-018

Every Contribution belongs to exactly one Occasion.

---

### BR-019

A Pledge is not equivalent to a received Contribution.

---

### BR-020

Every Expense must belong to a Budget Category.

---

### BR-021

Expenses cannot exist without an Occasion.

---

### BR-022

Financial summaries must always be derived from source transactions.

Summary values should never become the primary source of truth.

---

# Marketplace Domain

### BR-023

Every Vendor owns exactly one Vendor Profile.

---

### BR-024

Bookings may only be requested from approved Vendors.

---

### BR-025

Bookings cannot overlap when the Vendor has marked the same resource as unavailable.

---

### BR-026

Only completed Bookings may receive Reviews.

---

### BR-027

A Review may only be submitted by a verified customer of that Booking.

---

# Communication Domain

### BR-028

Announcements belong to an Occasion.

---

### BR-029

Notifications must reference an originating business event.

---

### BR-030

Deleted announcements remain available in audit history.

---

# Media Domain

### BR-031

Uploaded files belong to an owning entity.

No orphaned files are permitted.

---

### BR-032

Deleted media should follow the platform retention policy.

---

# Insights Domain

### BR-033

Health Score must always be calculated from live business data.

It must never be manually edited.

---

### BR-034

Reports should be reproducible from historical records.

---

# Cross-Domain Rules

### BR-035

Every business entity must have an owner.

---

### BR-036

Every significant action must create an Activity Log entry unless explicitly exempted.

---

### BR-037

Soft deletion should be preferred over permanent deletion for important business records.

---

### BR-038

Business identifiers must remain stable after creation.

---

### BR-039

Authorization decisions should depend on Occasion context rather than global roles whenever possible.

---

### BR-040

Business terminology must remain consistent across:

* User Interface
* APIs
* Documentation
* Database
* Source Code

---

# Rule Governance

Business Rules may only be changed when:

* Product requirements change.
* Business policy changes.
* Regulatory requirements change.

Implementation convenience is not a valid reason to modify a Business Rule.

---

# Related Documents

* Domain Model
* Product Scope
* PRD
* Engineering Playbook
* Architecture Decision Records
