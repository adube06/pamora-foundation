# Pamora UX Guidelines

**Version:** 1.0.0

**Status:** Mandatory

**Stability:** Controlled

---

# Purpose

This document defines the user experience (UX) principles that guide every interaction within Pamora.

The objective is to help users accomplish meaningful tasks with confidence, speed, and minimal effort.

---

# UX Philosophy

Pamora should help users organize important occasions without making planning feel complicated.

Every interaction should reduce uncertainty and increase user confidence.

---

# UX Principles

1. Guide, don't overwhelm.
2. Minimize user effort.
3. Make progress visible.
4. Prevent errors before they occur.
5. Recover gracefully from mistakes.
6. Keep users in control.
7. Reward progress.
8. Build trust through consistency.

---

# Primary User Journeys

The MVP focuses on these journeys:

## Host Journey

1. Register
2. Create Occasion
3. Invite Committee
4. Plan Tasks
5. Create Budget
6. Record Contributions
7. Track Expenses
8. Send Invitations
9. Complete Occasion

---

## Committee Journey

1. Receive Invitation
2. Join Occasion
3. View Assigned Tasks
4. Complete Tasks
5. Monitor Progress

---

## Guest Journey

1. Receive Invitation
2. View Occasion Details
3. RSVP
4. Receive Updates

---

## Vendor Journey (Post-MVP)

1. Register
2. Create Vendor Profile
3. Publish Services
4. Receive Quotation Request
5. Submit Quotation
6. Receive Booking

---

# Onboarding

First-time users should:

* Understand Pamora's purpose quickly.
* Complete registration easily.
* Create their first Occasion with guidance.
* Experience an early success within minutes.

Avoid lengthy tutorials before users take action.

---

# Progressive Learning

Introduce advanced features gradually.

Examples:

* Show basic planning first.
* Introduce budgeting after planning.
* Introduce reports after meaningful data exists.

Do not expose every capability on day one.

---

# Task-Oriented Design

Every screen should support a specific user goal.

Avoid pages that exist only to display information without enabling action.

---

# Error Prevention

Prevent mistakes through:

* Validation
* Sensible defaults
* Contextual guidance
* Confirmation for destructive actions

The best error is the one users never encounter.

---

# Error Recovery

When errors occur:

* Explain clearly.
* Preserve user input.
* Suggest recovery steps.
* Avoid blaming the user.

---

# Feedback

Users should always know:

* What happened.
* Why it happened.
* What they can do next.

Long-running actions should display progress indicators.

---

# Empty States

Empty states should:

* Explain the situation.
* Encourage the first action.
* Avoid making the interface feel broken.

---

# Notifications

Notifications should be:

* Relevant
* Timely
* Actionable

Avoid unnecessary interruptions.

---

# Search & Discovery

Help users find information through:

* Search
* Filters
* Sorting
* Recent items
* Clear navigation

Users should not rely solely on memory.

---

# Forms

Design forms to:

* Reduce typing
* Minimize required fields
* Group related information
* Auto-save where appropriate (future)

Large forms should be divided into logical steps.

---

# Mobile UX

Prioritize:

* One-handed use
* Large touch targets
* Clear navigation
* Fast loading
* Minimal text entry

---

# Desktop UX

Support:

* Keyboard shortcuts (future)
* Multi-column layouts
* Bulk actions
* Efficient workflows

---

# Accessibility

UX decisions must support users with varying abilities.

Design for:

* Screen readers
* Keyboard users
* Color blindness
* Low vision
* Reduced motion

Accessibility is part of the user experience.

---

# Trust & Confidence

Users should always understand:

* Who can see their information.
* Whether actions succeeded.
* Whether changes are saved.
* The status of important workflows.

Ambiguity reduces trust.

---

# Success Indicators

Measure UX success through:

* Task completion rate
* Time to complete key workflows
* Error rate
* User satisfaction
* Return usage
* Feature adoption

---

# Definition of Good UX

A user experience is considered successful when users can:

* Learn quickly.
* Complete tasks confidently.
* Recover from mistakes.
* Feel in control.
* Return without needing to relearn the interface.

---

# Architecture Note — Design for Completion (ADR-020)

The core UX rule of Pamora:

```text
User Starts Task
        │
        ▼
System Guides Progress
        │
        ▼
User Completes Task
        │
        ▼
System Confirms Success
```

Every important flow (creating an Occasion, recording a contribution, sending an invitation) should be designed to carry the user all the way to completion — not just present a form or a piece of information. See [ADR-020](../06-decisions/ADR-020-design-for-completion.md).

---

# Related Documents

* Design System
* UI Principles
* Accessibility Standards
* Brand Guidelines
* MVP Definition
