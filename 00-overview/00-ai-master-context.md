# AI Master Context

**Version:** 1.0.0

**Status:** Active

**Stability:** Frozen

**Last Updated:** July 2026

---

# Purpose

This document provides the permanent context for every AI assistant working on the Pamora platform.

It is the first document that must be read before reviewing requirements, writing code, designing user interfaces, or making architectural decisions.

Its purpose is to ensure that every AI assistant starts with the same understanding of the product.

---

# What is Pamora?

Pamora is an **Occasion Management Platform** built for East Africa.

It helps people plan, organize, coordinate, fund, execute, and preserve life's most important occasions.

Pamora is **not** an Event CRUD application.

It is a collaborative operating system for occasions.

An occasion becomes a shared digital workspace where everyone involved can work together.

---

# The Problem

People currently organize occasions using disconnected tools:

* WhatsApp groups
* Phone calls
* Excel spreadsheets
* Notebooks
* Printed invitation cards
* Mobile Money messages
* Personal reminders

These tools do not work together.

As a result:

* Tasks are forgotten.
* Budgets become difficult to track.
* Contributions are unclear.
* Communication becomes fragmented.
* Vendors are managed manually.
* Organizers experience unnecessary stress.

Pamora exists to replace this fragmented workflow with one trusted platform.

---

# Vision

To become Africa's most trusted operating system for planning, coordinating, funding, and preserving life's important occasions.

---

# Mission

To help individuals, families, communities, organizations, and businesses successfully organize meaningful occasions with greater confidence, transparency, and coordination.

---

# Product Philosophy

Every engineering decision should support the following principles:

* Simplicity before complexity.
* Business before technology.
* Collaboration before individual effort.
* Trust before convenience.
* Long-term maintainability before short-term speed.

---

# Core Product Concept

The core business entity is the **Occasion**.

Everything in Pamora exists because of an Occasion.

Examples:

* Wedding
* Funeral
* Birthday
* Graduation
* Conference
* Community Fundraiser
* Religious Celebration
* Corporate Event

If a feature does not improve the management of an Occasion, it should be questioned.

---

# Primary Users

Pamora supports multiple user contexts.

A single person may simultaneously be:

* Occasion Host
* Committee Member
* Treasurer
* Guest
* Vendor
* Service Provider

Permanent business roles should be avoided whenever possible.

Permissions depend on context.

---

# Core Business Domains

Pamora is divided into the following domains:

## Identity

Authentication, profiles, permissions, and account management.

## Occasion

The central domain responsible for the lifecycle of every occasion.

## People

Guests, committee members, invitations, RSVPs, and participant management.

## Planning

Tasks, timelines, milestones, checklists, and execution tracking.

## Finance

Budgets, contributions, expenses, fundraising, and financial transparency.

## Marketplace

Vendor discovery, bookings, availability, catalogues, and reviews.

## Communication

Announcements, notifications, reminders, invitations, and updates.

## Media

Photos, videos, documents, invitations, and memories.

## Intelligence

Insights, analytics, reports, health score, recommendations, and future AI capabilities.

---

# Product Scope

Pamora is designed as a platform rather than a single feature.

Capabilities include:

* Occasion planning
* Digital invitations
* RSVP management
* Committee collaboration
* Budget planning
* Contribution tracking
* Vendor marketplace
* Booking management
* Task management
* Timeline management
* Communication
* Media storage
* Reporting
* Analytics

Future capabilities include:

* Integrated payments
* AI planning assistant
* Organizational accounts
* Enterprise offerings
* Public APIs

---

# Engineering Philosophy

Technology exists to support business goals.

Business terminology should appear consistently across:

* Code
* Database
* APIs
* Documentation
* User Interface

Architecture decisions must prioritize clarity, scalability, maintainability, and correctness.

---

# Non-Negotiable Rules

Every AI assistant working on Pamora must follow these rules:

1. Do not redesign the product.
2. Do not invent new features.
3. Do not change approved business rules.
4. Do not introduce breaking architectural changes.
5. Always use the established business terminology.
6. Follow the Pamora Constitution.
7. Follow the Engineering Playbook.
8. Prefer maintainability over cleverness.
9. Ask for clarification instead of making assumptions.
10. Keep business logic independent of framework-specific code.

---

# Definition of Success

Success is **not** measured by:

* Number of screens
* Lines of code
* Number of APIs
* Number of features

Success is measured by the number of occasions that are successfully planned and completed using Pamora.

---

# Source of Truth

Implementation must always follow this order:

1. AI Master Context
2. Constitution
3. Engineering Playbook
4. Product Requirements
5. Architecture Documents
6. Current Sprint Specification
7. Implementation

No implementation should contradict documents higher in this hierarchy.

---

# Final Directive

Pamora is a long-term product.

Every implementation decision should increase:

* Trust
* Simplicity
* Scalability
* Collaboration
* Maintainability

If a proposed solution weakens any of these principles, it should be reconsidered before implementation.
