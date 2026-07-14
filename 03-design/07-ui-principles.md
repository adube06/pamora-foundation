# Pamora UI Principles

**Version:** 1.0.0

**Status:** Mandatory

**Stability:** Frozen

---

# Purpose

This document defines the visual and interaction principles that govern every interface in Pamora.

It ensures users experience a consistent, intuitive, and trustworthy interface across web, mobile, and administrative products.

---

# Core Principles

1. Show what matters first.
2. Keep interfaces focused.
3. Reduce unnecessary choices.
4. Guide users toward completion.
5. Prefer recognition over recall.
6. Design for confidence.
7. Keep interactions predictable.
8. Never surprise the user.

---

# Information Hierarchy

Every screen should answer these questions immediately:

1. Where am I?
2. What can I do here?
3. What is most important?
4. What requires my attention?
5. What should I do next?

Primary actions must be visually dominant.

Secondary actions should never compete with primary actions.

---

# Layout Principles

Every screen should have:

* Clear page title
* Primary action
* Context information
* Main content area
* Secondary information
* Optional supporting panel

Avoid visual clutter.

Whitespace is intentional and should improve readability.

---

# Navigation Principles

Navigation must be:

* Consistent
* Predictable
* Discoverable
* Minimal

Users should never need to guess where a feature is located.

Navigation patterns should remain stable across releases.

---

# Visual Hierarchy

Use hierarchy through:

* Typography
* Size
* Spacing
* Contrast
* Position

Avoid relying on color alone to communicate importance.

---

# Progressive Disclosure

Present only the information needed for the current task.

Reveal advanced options only when required.

Do not overwhelm first-time users.

---

# Forms

Forms should:

* Minimize required fields
* Group related information
* Validate immediately where appropriate
* Preserve entered data after validation errors

The primary action should remain visible.

---

# Buttons

Each screen should have:

* One primary action
* Limited secondary actions
* Destructive actions clearly distinguished

Avoid multiple competing primary buttons.

---

# Feedback

Every user action should provide clear feedback.

Examples:

* Success confirmation
* Validation errors
* Loading indicators
* Progress updates
* Failure explanations

Feedback should be immediate and understandable.

---

# Empty States

An empty screen should explain:

* Why it is empty.
* What the user can do next.
* The primary action available.

Every empty state should encourage progress.

---

# Loading States

Loading indicators should:

* Appear quickly
* Match expected wait time
* Preserve layout stability

Use skeleton screens for content-heavy interfaces where appropriate.

---

# Error States

Errors should:

* Explain the problem.
* Avoid technical jargon.
* Suggest a recovery action.
* Preserve user input whenever possible.

---

# Confirmation

Require confirmation only for:

* Destructive actions
* Irreversible actions
* High-impact operations

Avoid excessive confirmation dialogs.

---

# Search

Search should:

* Be fast
* Be forgiving
* Support partial matches
* Provide useful empty results

Search should not replace good navigation.

---

# Tables

Tables should:

* Support sorting
* Support filtering
* Support pagination
* Display totals where useful
* Remain readable on smaller screens

Prefer cards over tables on mobile devices.

---

# Mobile Principles

Mobile interfaces should prioritize:

* Thumb-friendly controls
* Simple navigation
* Minimal typing
* Clear hierarchy
* Fast interactions

Critical actions should be reachable without excessive scrolling.

---

# Desktop Principles

Desktop interfaces may:

* Display more contextual information
* Support multi-column layouts
* Provide advanced filtering
* Enable efficient keyboard workflows

Avoid wasting available screen space.

---

# Consistency

Users should encounter the same:

* Terminology
* Icons
* Colors
* Interaction patterns
* Feedback styles

Consistency reduces learning time.

---

# Accessibility

UI decisions must support:

* Keyboard navigation
* Screen readers
* High contrast
* Reduced motion
* Color accessibility

Accessibility is a design requirement, not a post-release enhancement.

---

# Trust

Interfaces should communicate trust through:

* Predictable behavior
* Accurate information
* Clear permissions
* Transparent status indicators
* Reliable feedback

The interface should never mislead users.

---

# Definition of Good UI

A screen is considered complete when users can:

* Understand its purpose immediately.
* Complete the intended task confidently.
* Recover from mistakes easily.
* Navigate without confusion.
* Receive clear feedback.

---

# Architecture Note — One Primary Action Per Screen (ADR-019)

The base rule of Pamora UI:

```text
Screen
   │
   ├── Primary Action (1)
   ├── Secondary Actions (few)
   └── Contextual Actions (optional)
```

Example — Occasion Dashboard:

* ✅ **Create Task** (Primary)
* Secondary: Invite Member
* Secondary: View Budget
* Contextual: Export Report

Not this:

* Create Task
* Add Expense
* Send Announcement
* Add Vendor
* Upload Media

...all carrying equal visual weight.

This reduces cognitive load and helps the user know what to do next. See [ADR-019](../06-decisions/ADR-019-one-primary-action-per-screen.md).

---

# Related Documents

* Design System
* UX Guidelines
* Accessibility Standards
* Brand Guidelines
* Engineering Playbook
