# ADR-005 — Marketplace Architecture (Vendor ≠ Service ≠ Booking)

**Status:** Accepted

**Date:** 2026-07-13

**Domain(s):** Marketplace

---

# Context

Pamora's Marketplace is strategically positioned as a **Vendor Operating System**, not a directory — vendors should be able to run their business through Pamora, which is what keeps them on the platform even between bookings. A schema that conflates Vendor, Service, and Booking into one shape cannot support this: it can't represent a vendor offering multiple distinct services, mixing fixed-price services with rental inventory, or a booking referencing a specific offering rather than "the vendor" in general.

---

# Decision

Vendor, Service, and Booking remain three fully distinct concepts:

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

A Booking always references the specific Service or Rental Item involved, not the Vendor alone.

---

# Consequences

* Supports multi-service vendors (e.g. one Vendor offering DJ, MC, and Sound System services simultaneously).
* Supports vendors that mix fixed-price services and rental inventory in one profile.
* Enables future package deals, dynamic pricing, and inventory-aware search without a schema rewrite.
* Availability and double-booking checks (BR-025) operate at the Service/Rental Item level, not the Vendor level.
* Slightly more upfront modeling complexity than a flat "vendor with a price" schema, but this is the foundation the Vendor Operating System positioning depends on.

---

# Related Documents

* [Marketplace PRD](../02-product/prd/05-marketplace.md)
* [Business Rules](../02-product/05-business-rules.md) — BR-023 through BR-027
* [Value Proposition](../01-business/04-value-proposition.md)
