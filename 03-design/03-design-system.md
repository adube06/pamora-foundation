# Pamora Design System

**Version:** 1.0.0

**Status:** Mandatory

**Stability:** Mixed — the tokens-before-components principle ([ADR-018](../06-decisions/ADR-018-tokens-before-components.md)) is Frozen; specific token values (exact colors, spacing scale, component list) are Living and expected to evolve.

---

# Purpose

The Pamora Design System provides a unified visual and interaction language for all Pamora products.

It ensures consistency across:

* Web Application
* Mobile Application
* Admin Portal
* Marketing Website

The Design System is the single source of truth for UI components and visual standards.

---

# Design Principles

1. Clarity over decoration.
2. Consistency across platforms.
3. Accessibility by default.
4. Mobile-first thinking.
5. Responsive layouts.
6. Fast interactions.
7. Minimal cognitive load.
8. Progressive disclosure.

---

# Design Tokens

All visual values must originate from design tokens.

## Color Tokens

Use semantic colors instead of hard-coded values.

Examples:

* Primary
* Secondary
* Success
* Warning
* Error
* Info
* Surface
* Background
* Border
* Text Primary
* Text Secondary

Color values should be defined in a shared token source.

---

## Typography Tokens

Primary font:

* Inter (default)

Fallback:

* System UI fonts

Scale:

* Display
* Heading 1
* Heading 2
* Heading 3
* Title
* Body
* Caption
* Label

Typography should follow a consistent spacing rhythm.

---

## Spacing Tokens

Use an 8-point spacing system.

Base values:

```text
4
8
16
24
32
40
48
64
80
96
```

Avoid arbitrary spacing values.

---

## Radius Tokens

Examples:

* Small
* Medium
* Large
* Extra Large
* Pill

Maintain consistency across all components.

---

## Elevation

Use predefined elevation levels.

Examples:

* Level 0
* Level 1
* Level 2
* Level 3
* Modal

Avoid excessive shadows.

---

# Layout System

Responsive breakpoints:

* Mobile
* Tablet
* Desktop
* Large Desktop

Layouts should adapt gracefully without changing core functionality.

---

# Grid

Desktop:

* 12-column grid

Tablet:

* 8-column grid

Mobile:

* Single-column adaptive layout

---

# Component Library

Core components include:

* Button
* Icon Button
* Input
* Textarea
* Select
* Checkbox
* Radio
* Toggle
* Badge
* Avatar
* Card
* Table
* Tabs
* Modal
* Drawer
* Toast
* Alert
* Tooltip
* Breadcrumb
* Pagination
* Empty State
* Skeleton Loader

No custom component should duplicate an existing component's purpose.

---

# Buttons

Types:

* Primary
* Secondary
* Ghost
* Danger
* Link

States:

* Default
* Hover
* Focus
* Active
* Disabled
* Loading

---

# Forms

Every form should provide:

* Labels
* Helper text
* Validation messages
* Required indicators
* Accessible keyboard navigation

Avoid placeholder-only labels.

---

# Icons

Use a single icon library consistently.

Icons should communicate meaning, not decoration.

---

# Navigation

Navigation patterns:

* Top Navigation
* Sidebar
* Bottom Navigation (Mobile)
* Breadcrumbs
* Context Menus

Navigation should remain predictable across products.

---

# Tables

Tables should support:

* Sorting
* Filtering
* Pagination
* Empty states
* Loading states

Large datasets should avoid rendering unnecessary rows.

---

# Feedback Components

Provide consistent feedback for:

* Success
* Warning
* Error
* Information
* Loading

Feedback should always explain what happened and what the user can do next.

---

# Motion

Animations should:

* Support understanding
* Be subtle
* Be performant

Avoid decorative motion.

Respect reduced-motion user preferences.

---

# Empty States

Every empty state should include:

* Explanation
* Primary action
* Optional secondary guidance

Avoid blank screens.

---

# Responsive Design

All interfaces must support:

* Small phones
* Large phones
* Tablets
* Desktop

Functionality must remain consistent across devices.

---

# Dark Mode

The design system must support:

* Light theme
* Dark theme

Themes should share the same component structure.

---

# Documentation

Every component must document:

* Purpose
* Variants
* States
* Accessibility
* Usage examples
* Do's and Don'ts

---

# Definition of a Design System Component

A component is complete when it includes:

* Design specification
* Interaction rules
* Accessibility guidance
* Responsive behavior
* Implementation reference
* Test scenarios

---

# Architecture Note — Tokens Before Components (ADR-018)

The base rule of the Design Foundation:

```text
Design Tokens
        │
        ▼
Component Library
        │
        ▼
Pages
        │
        ▼
Features
```

This means:

* No component invents its own color, spacing, or typography.
* React and Flutter both consume the same base tokens.
* Changing a token (e.g. Primary Color or Border Radius) updates the look of the entire system without touching every component.

See [ADR-018](../06-decisions/ADR-018-tokens-before-components.md).

---

# Related Documents

* Information Architecture
* UI Principles
* UX Guidelines
* Accessibility Standards
* Brand Guidelines
