# Pamora Foundation

> **Official Product & Engineering Knowledge Base**

---

## Overview

Pamora Foundation is the official source of truth for the Pamora platform.

It contains every business, product, design, engineering, and architectural decision that defines how Pamora is built and evolves.

This repository exists to ensure that every developer, designer, AI assistant, product manager, and stakeholder works from the same understanding of the product.

If a decision is not documented here, it should not be considered an official part of Pamora.

---

# About Pamora

Pamora is an Occasion Management Platform designed for East Africa.

It enables people to plan, coordinate, fund, and successfully execute life's most important occasions from a single platform.

Unlike traditional event management applications, Pamora is built around the concept of an **Occasion**, not simply an event.

An occasion is treated as a complete operational workspace where organizers, committee members, guests, contributors, vendors, and service providers collaborate.

Examples include:

* Weddings
* Funerals
* Birthdays
* Graduation Ceremonies
* Religious Celebrations
* Community Fundraisers
* Corporate Events
* Conferences
* Family Gatherings

---

# Vision

To become Africa's most trusted operating system for planning, coordinating, funding, and preserving life's important occasions.

---

# Mission

To reduce the stress of organizing important occasions by providing one trusted digital platform that connects people, planning, finances, communication, and vendors.

---

# Product Philosophy

Pamora is built on five principles:

* Business before technology.
* Simplicity over complexity.
* Trust above everything.
* Collaboration instead of chaos.
* Long-term maintainability over short-term convenience.

---

# Repository Structure

```text
00-overview/
Business vision and product identity.

01-business/
Business strategy and commercial knowledge.

02-product/
Product requirements and business rules.

03-design/
User experience and design system.

04-engineering/
Architecture and implementation guidance.

05-ai/
AI instructions and prompt library.

06-decisions/
Architecture Decision Records (ADRs).

diagrams/
Architecture, ERD and workflow diagrams.

templates/
Reusable templates.
```

---

# Intended Audience

This repository is intended for:

* Software Engineers
* Mobile Developers
* Backend Developers
* Product Managers
* UI/UX Designers
* QA Engineers
* AI Coding Assistants
* Technical Writers
* Business Stakeholders

---

# Source of Truth

The documents in this repository are the official reference for the Pamora platform.

Implementation must always follow this order:

1. AI Master Context
2. Constitution
3. Engineering Playbook
4. Product Requirements
5. Architecture Documents
6. Current Sprint Specification
7. Implementation

Business requirements always take precedence over implementation convenience.

---

# Documentation Standards

Every document in this repository follows a common structure:

* Purpose
* Scope
* Definitions
* Principles
* Detailed Specification
* Examples
* Edge Cases
* Related Documents
* Revision History

---

# Stability Model

Not every decision in this Foundation is equally expensive to change, and not every change carries the same risk. Every document carries a **Stability** tag alongside its Version and Status, using one of three categories:

## Frozen

Domain boundaries, identity models, aggregate roots, financial consistency (ledger architecture), business rules, and core architectural/engineering standards (security, database, API contracts, coding standards).

These are one-way-door decisions: expensive or risky to change once real users, real data, or real financial history exist on top of them.

**Changing a Frozen document requires a new or updated ADR and architectural review.** Implementation convenience is never a valid reason to bypass one.

## Controlled

Business strategy (market analysis, personas, GTM, revenue phasing), release scope and sequencing (MVP slice, roadmap), and durable-but-not-architectural product/design standards (UI Principles, UX Guidelines, Accessibility, Brand Guidelines, Components, specific design token values, operational budgets like Performance and Observability targets, the AI Prompt Library).

These aren't one-way doors, but they aren't casual edits either — changing them has ripple effects across teams or across the product's consistency, so they require a deliberate documentation update plus review (design review for product/design documents, leadership review for business-strategy documents). **No ADR is required**, but an update should not happen silently.

## Living

UX flows, screens, onboarding, task flows, contribution flows, specific journeys, navigation, and the feature/acceptance-criteria/edge-case catalogs.

These are two-way-door decisions: they are *expected* to evolve once real users interact with the product. Observed behavior is evidence, not a violation of the Foundation.

**Living documents can be updated directly** as evidence comes in — no ADR, no review gate required. Just keep the document in sync with what actually shipped.

## Mixed

A small number of documents contain more than one category in a single file (for example, a domain PRD defines Frozen entities/events alongside Controlled functional requirements and Living illustrative UX flow examples). These carry a `Mixed` tag with an inline note or a cross-reference identifying which sections are which.

## Why this exists

The Foundation is meant to protect the decisions that are genuinely hard to unwind — not to freeze the user experience or the business strategy before a single real user has touched the product. Sequencing is: **Foundation → MVP → Real Usage → Observation → Iteration → Product-Market Fit.** The Stability tag makes explicit, at a glance, which category a given document falls into, and what process (ADR, review, or direct update) governs changing it — so that iteration on Living and Controlled documents never feels like, or requires, relitigating the Frozen ones.

---

# Contributing

Every significant product or engineering decision must be documented before implementation.

Architecture changes require an Architecture Decision Record (ADR).

Business rule changes require updates to the Product documentation.

Breaking API changes require versioning.

Undocumented implementation is not considered complete.

---

# Repository Status

Current Version:

**Pamora Foundation v1.0**

Status:

**Under Active Development**

---

# License

This repository contains proprietary product documentation for Pamora.

All rights reserved unless otherwise specified.

---

*"Great software starts with shared understanding before shared code."*
