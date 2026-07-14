# Pamora Brand Guidelines

**Version:** 1.0.0

**Status:** Mandatory

---

# Purpose

This document defines the visual identity, communication style, and branding standards for Pamora.

Every public-facing asset should follow these guidelines to maintain a consistent and recognizable brand.

---

# Brand Vision

Pamora helps people organize life's important occasions with confidence, simplicity, and collaboration.

The brand should communicate:

* Trust
* Simplicity
* Reliability
* Celebration
* Organization
* Professionalism

---

# Brand Personality

Pamora is:

* Helpful
* Calm
* Modern
* Reliable
* Friendly
* Organized
* Human

Pamora is not:

* Loud
* Overly playful
* Aggressive
* Confusing
* Overly technical

---

# Brand Voice

Communication should be:

* Clear
* Friendly
* Direct
* Encouraging
* Respectful

Avoid:

* Unnecessary jargon
* Blameful language
* Ambiguous instructions
* Excessive marketing language

---

# Logo

The logo should always remain:

* Clear
* Readable
* Properly spaced
* Consistent

Never:

* Stretch
* Distort
* Rotate
* Change proportions
* Add effects
* Place on unreadable backgrounds

---

# Logo Clear Space

Maintain a minimum clear space around the logo equal to the height of the "P" in the primary logo.

No other visual elements should enter this area.

---

# Logo Variants

Supported variants:

* Full color
* Monochrome
* White
* Icon-only (where appropriate)

Use the appropriate version based on the background and available space.

---

# Color Palette

Primary

* Brand Primary
* Brand Secondary

Supporting

* Success
* Warning
* Error
* Information

Neutral

* Surface
* Background
* Border
* Text Primary
* Text Secondary
* Disabled

All color values must originate from the shared design tokens.

---

# Typography

Primary Typeface

* Inter

Fallback

* System UI fonts

Typography hierarchy:

* Display
* H1
* H2
* H3
* Title
* Body
* Caption
* Label

Maintain consistent spacing and line height.

---

# Iconography

Use one icon family across all products.

Icons should:

* Be simple
* Be recognizable
* Match visual weight
* Support user understanding

Avoid mixing multiple icon styles.

---

# Illustrations

Illustrations should:

* Support understanding
* Feel modern
* Represent diverse users
* Avoid unnecessary complexity

Illustrations should never replace essential instructions.

---

# Photography

Images should reflect:

* Authentic moments
* Diversity
* Collaboration
* Celebration
* Real environments

Avoid generic or misleading imagery.

---

# Buttons

Primary actions should always use the primary button style.

Secondary actions should use the approved secondary styles.

Do not invent custom button styles.

---

# Forms

Forms should follow the Design System.

Maintain:

* Consistent spacing
* Labels
* Validation styles
* Input states

---

# Notifications

Use consistent visual language for:

* Success
* Error
* Warning
* Information

Messaging should be concise and actionable.

---

# Marketing Materials

All public materials should use:

* Approved colors
* Approved typography
* Approved logo usage
* Consistent imagery
* Brand voice

Consistency strengthens recognition.

---

# Documentation

Internal documentation should:

* Use brand typography where applicable.
* Maintain visual consistency.
* Use approved terminology.

---

# Naming Conventions

Product names, feature names, and terminology should remain consistent across:

* UI
* Documentation
* APIs
* Marketing
* Support

Terminology changes require documentation updates.

---

# Localization

Brand tone should remain consistent across supported languages.

Translations should prioritize clarity over literal wording.

---

# Definition of On-Brand

A deliverable is considered on-brand when it:

* Uses approved visual assets.
* Follows design tokens.
* Uses the correct terminology.
* Reflects Pamora's personality.
* Maintains visual consistency across platforms.

---

# Architecture Note — One Brand, Many Platforms (ADR-022)

The base rule of the Brand Foundation:

```text
Brand Identity
       │
       ▼
Design Tokens
       │
       ▼
Web
Mobile
Admin
Documentation
Marketing
Presentations
Emails
Social Media
```

Regardless of whether a user encounters Pamora through the Web App, the Flutter App, the Landing Page, an Email, a PDF, a Presentation, or Social Media, they should immediately recognize it as the same Pamora product. See [ADR-022](../06-decisions/ADR-022-one-brand-many-platforms.md).

---

# Related Documents

* Design System
* UI Principles
* UX Guidelines
* Accessibility Standards
* Marketing Assets
