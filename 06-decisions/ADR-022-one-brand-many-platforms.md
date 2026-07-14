# ADR-022 — One Brand, Many Platforms

**Status:** Accepted

**Date:** 2026-07-14

**Domain(s):** Brand Guidelines (cross-cutting)

---

# Context

Pamora reaches users through many surfaces beyond the web and mobile apps themselves — landing pages, emails, PDFs, presentations, social media. Each of these is often produced by a different tool or team, and without a shared rule, they tend to drift toward inconsistent colors, typography, and tone, even when the underlying Design Tokens (see [ADR-018](ADR-018-tokens-before-components.md)) are followed correctly inside the product itself.

---

# Decision

Brand identity flows through Design Tokens into every surface Pamora appears on, not just the product UI:

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

Regardless of whether a user encounters Pamora through the Web App, the Flutter App, the Landing Page, an Email, a PDF, a Presentation, or Social Media, they should immediately recognize it as the same Pamora product.

---

# Consequences

* Brand Guidelines' color, typography, and logo rules apply outside the codebase too — marketing materials, decks, and support documents are held to the same "on-brand" bar as the product UI (Brand Guidelines' "Definition of On-Brand").
* Non-engineering outputs (a pitch deck, a support email template) should still trace back to the same Design Tokens as the product, even though they aren't rendered by React or Flutter — in practice this means referencing brand color hex values and font files exported from the token source, not eyeballing them.
* Extends [ADR-018](ADR-018-tokens-before-components.md)'s "tokens before components" principle one layer further: tokens are the source of truth not just for components, but for brand presence anywhere Pamora shows up.
* Requires whoever produces off-product assets (marketing, support, partnerships) to have access to the current Brand Guidelines and token values — this is a distribution/process requirement, not just an engineering one.

---

# Related Documents

* [Brand Guidelines](../03-design/09-brand-guidelines.md)
* [ADR-018 — Tokens Before Components](ADR-018-tokens-before-components.md)
* [Design System](../03-design/03-design-system.md)
