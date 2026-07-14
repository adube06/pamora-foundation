# Marketplace Domain PRD

**Version:** 1.0.0

**Status:** Approved

---

# 1. Purpose

The Marketplace Domain connects Occasion Hosts with trusted Vendors.

It enables vendor discovery, availability management, quotations, bookings, rentals, service delivery, and verified reviews.

The Marketplace is fully integrated into the Occasion Workspace.

Its objective is to help users successfully procure everything required for an Occasion.

---

# 2. Business Goals

Enable Hosts to:

* Discover vendors.
* Compare services.
* Request quotations.
* Book vendors.
* Track vendor commitments.
* Review completed work.

Enable Vendors to:

* Showcase services.
* Receive qualified leads.
* Manage bookings.
* Track availability.
* Grow reputation.
* Build repeat business.

---

# 3. Scope

The Marketplace Domain owns:

* Vendor
* Vendor Business Profile
* Services
* Rental Catalog
* Availability
* Quotations
* Bookings
* Reviews
* Vendor Portfolio

It does **not** own:

* Payments
* Budgets
* Invitations
* User Authentication
* Occasion Lifecycle

---

# 4. Core Entities

## Vendor

Represents a registered business.

Required information:

* Business Name
* Owner
* Verification Status
* Categories
* Service Areas
* Contact Information
* Rating
* Status

---

## Service

Represents a fixed-price or custom service.

Examples:

* Photography
* DJ
* MC
* Catering
* Decoration
* Makeup
* Live Band

Each service includes:

* Pricing Model
* Description
* Gallery
* Estimated Duration

---

## Rental Item

Represents rentable inventory.

Examples:

* Chairs
* Tables
* Tents
* Sound Systems
* Vehicles
* Lighting

Attributes include:

* Quantity Available
* Unit Price
* Availability Rules

---

## Quotation

Represents a formal offer from a Vendor.

States:

* Draft
* Submitted
* Accepted
* Rejected
* Expired

A quotation may become a Booking.

---

## Booking

Represents an agreement between an Occasion and a Vendor.

States:

```text
Requested
    │
    ▼
Accepted
    │
    ▼
Confirmed
    │
    ▼
In Progress
    │
    ▼
Completed
```

Alternative paths:

```text
Requested
   ├── Declined
   ├── Cancelled
   └── Expired
```

---

## Review

Represents customer feedback.

Only verified customers may submit reviews.

Reviews become part of the Vendor reputation.

---

# 5. Functional Requirements

## FR-001 — Vendor Registration

Businesses may apply to become Vendors.

Applications require administrative approval before public listing.

---

## FR-002 — Publish Services

Approved Vendors may publish one or more Services.

Services remain editable while active.

---

## FR-003 — Manage Rental Inventory

Rental Vendors may define inventory quantities and availability.

Inventory reservations should prevent double-booking.

---

## FR-004 — Request Quotation

Hosts may request quotations from one or more Vendors.

Quotation requests belong to a specific Occasion.

---

## FR-005 — Submit Quotation

Vendors may submit detailed quotations.

Hosts receive notifications upon submission.

---

## FR-006 — Confirm Booking

Accepted quotations may become confirmed Bookings.

Confirmation reserves Vendor availability.

---

## FR-007 — Complete Booking

Completed Bookings become eligible for Reviews.

---

## FR-008 — Leave Review

Only verified customers of completed Bookings may submit Reviews.

Reviews become immutable after publication unless moderated.

---

# 6. Availability Management

Every Vendor maintains an availability calendar.

Availability must account for:

* Existing bookings
* Rental inventory
* Maintenance periods
* Manual blocking
* Public holidays (future)

Availability checks occur before booking confirmation.

---

# 7. Vendor Reputation

Reputation is based on:

* Verified reviews
* Booking completion rate
* Response time
* Cancellation rate
* Profile completeness
* Verification status

Overall ratings should not rely solely on star averages.

---

# 8. Domain Events

The Marketplace Domain emits:

* VendorApplied
* VendorApproved
* ServicePublished
* QuotationRequested
* QuotationSubmitted
* BookingRequested
* BookingConfirmed
* BookingCompleted
* ReviewPublished

---

# 9. Integrations

Occasion Domain

* Booking ownership

Planning Domain

* Vendor-related Tasks

Finance Domain

* Vendor costs
* Budget comparison

Communication Domain

* Booking notifications

Media Domain

* Portfolio images
* Service galleries

Insights Domain

* Vendor analytics
* Marketplace performance

---

# 10. Permissions

Vendor capabilities include:

* Manage Profile
* Publish Services
* Manage Inventory
* Submit Quotations
* Confirm Bookings
* Manage Availability
* Respond to Reviews (future)

Host capabilities include:

* Browse Vendors
* Request Quotations
* Confirm Bookings
* Leave Reviews

---

# 11. Reporting

Marketplace metrics include:

* Active Vendors
* Booking Requests
* Booking Conversion Rate
* Completion Rate
* Average Response Time
* Most Booked Categories
* Vendor Utilization

---

# 12. Success Metrics

The Marketplace succeeds when:

* Hosts quickly find trusted Vendors.
* Vendors receive qualified business opportunities.
* Booking completion rates remain high.
* Verified reviews build marketplace trust.

---

# 13. Future Enhancements

Potential capabilities:

* Dynamic pricing
* Instant booking
* Package bundles
* Vendor teams
* AI vendor recommendations
* Route planning
* Contract generation
* Escrow payments
* Dispute resolution
* Multi-city operations

---

# Strategic Decision — Marketplace as a Vendor Operating System

Pamora's Marketplace is not a "directory." It is not just a place to search for a vendor.

It is a **Vendor Operating System**.

A Vendor should be able to run their business through Pamora. This is what keeps vendors on the platform even when they have no booking today.

---

# Architecture Note — Vendor, Service, and Booking (ADR-005)

`Vendor ≠ Service ≠ Booking`

These must remain three fully distinct concepts.

```text
Vendor
│
├── Services
│
├── Rental Inventory
│
├── Availability
│
└── Quotations
        │
        ▼
    Booking
```

Do not put all information onto `vendors` or `bookings`.

For example:

* One Vendor can offer DJ, MC, and Sound System services at the same time.
* A Vendor can have fixed-price services and rental inventory simultaneously.
* A Booking should reference the specific Service or Rental Item, not the Vendor alone.

This allows for:

* Multi-service vendors.
* Rental businesses.
* Package deals (future).
* Smart search.
* Dynamic pricing.
* Inventory management.

This is the foundation that makes the Marketplace a Vendor Operating System rather than a business directory. See [ADR-005](../../06-decisions/ADR-005-marketplace-architecture.md).

---

# Related Documents

* Occasion PRD
* Finance PRD
* Communication PRD
* Business Rules
* Domain Model
