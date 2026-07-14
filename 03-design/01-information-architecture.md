# Information Architecture

**Version:** 1.0.0

**Status:** Approved

---

# Purpose

This document defines the structural organization of the Pamora platform.

It describes how information is grouped, navigated, and accessed across mobile, web, and administrative interfaces.

The architecture should remain stable as the platform evolves.

---

# Product Structure

Pamora consists of four primary experiences:

1. Public Experience
2. Mobile App
3. Vendor Workspace
4. Admin Portal

Each experience serves different users while sharing the same business domains.

---

# Public Experience

Accessible without authentication.

## Sections

* Home
* Public Occasion Page
* Digital Invitation
* RSVP
* Contribution Page
* Public Vendor Profile
* Vendor Directory
* About
* Help

---

# Mobile Application

Primary application for registered users.

## Main Navigation

```text
Home
Occasions
Marketplace
Notifications
Profile
```

---

# Home

Purpose:

Provide a personalized overview.

Contains:

* Active Occasions
* Upcoming Tasks
* Budget Snapshot
* Recent Activity
* Notifications
* Suggested Actions

---

# Occasions

The central workspace.

Contains:

* Dashboard
* Details
* Committee
* Guests
* Invitations
* Planning
* Timeline
* Finance
* Vendors
* Gallery
* Announcements
* Documents
* Activity Log
* Settings

---

# Marketplace

Contains:

* Categories
* Search
* Nearby Vendors
* Featured Vendors
* Bookings
* Reviews
* Saved Vendors

---

# Notifications

Contains:

* System Notifications
* Booking Updates
* Task Reminders
* RSVP Updates
* Contribution Alerts
* Announcements

---

# Profile

Contains:

* Personal Profile
* Verification
* Preferences
* Payment Methods (Future)
* Privacy
* Security
* My Reviews
* Support

---

# Occasion Workspace

Each Occasion acts as an independent workspace.

## Workspace Navigation

```text
Overview
Committee
Guests
Planning
Finance
Marketplace
Timeline
Media
Announcements
Activity
Settings
```

---

# Vendor Workspace

Vendor-specific functionality.

## Navigation

```text
Dashboard
Bookings
Services
Rental Inventory
Availability
Reviews
Analytics
Profile
Settings
```

---

# Admin Portal (Filament)

Administrative management.

## Navigation

```text
Dashboard
Users
Occasions
Vendors
Bookings
Reviews
Payments
Reports
CMS
Support
Settings
Audit Logs
```

---

# Cross-Cutting Features

Available throughout the platform:

* Search
* Notifications
* Global Activity Feed
* File Uploads
* User Mentions
* Help
* Feedback

---

# Search Architecture

Global search should support:

* Occasions
* Vendors
* Guests
* Committee Members
* Tasks
* Bookings
* Documents

Search results should respect authorization rules.

---

# Navigation Principles

Navigation should:

* Be predictable.
* Minimize taps.
* Preserve context.
* Avoid duplicate destinations.
* Scale with additional modules.

---

# URL Structure (Public)

Examples:

```text
/e/{occasion-slug}
/v/{vendor-slug}
/invite/{token}
/rsvp/{token}
```

These URLs should remain stable over time.

---

# Mobile Navigation Principles

Primary navigation should expose only the highest-level business domains.

Secondary features should exist within their parent workspace.

Avoid deep navigation hierarchies.

---

# Future Extensions

Future modules may include:

* AI Assistant
* Organization Workspace
* Partner Portal
* Payment Center
* Public APIs
* Integrations Marketplace

These should integrate without restructuring existing navigation.

---

# Information Architecture Principles

* Occasion is the primary organizational unit.
* Marketplace extends the Occasion.
* Navigation follows business domains.
* Users should always know where they are.
* Context should never be lost while switching features.

---

# Related Documents

* Domain Model
* Product Scope
* Business Rules
* User Journeys
* Design System
* PRD
