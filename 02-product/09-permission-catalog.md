# Canonical Permission Catalog

**Version:** 1.0.0

**Status:** Approved

**Stability:** Frozen

---

# Purpose

Every domain PRD describes permissions informally, in its own words, in its own "Permissions" or "Security" section. Left alone, this produces permission drift: two engineers implementing two domains independently will invent two different naming conventions, two different granularities, and eventually two permissions that mean the same thing but don't share a name.

This document is the single source of truth for permission strings across Pamora. A domain PRD's "Permissions" section describes *what a role needs to be able to do*, in plain language; this catalog is the *actual enforceable string* that implements it. When they appear to disagree, this catalog wins.

This document is tagged Frozen — it is an authorization contract, not a UX artifact. Adding, renaming, or removing a permission requires updating this catalog directly (a documentation change is enough; a new permission does not require an ADR unless it also changes a Frozen entity or aggregate boundary elsewhere).

---

# Naming Convention

```text
{domain}.{action}
```

* `{domain}` is always one of the 9 Core Business Domain names (lowercase), matching the [Domain Model](../04-engineering/04-domain-model.md) exactly. Integrations, being a Supporting Technical Domain with no business data, has no permissions of its own.
* `{action}` is a snake_case verb or verb_noun describing the capability, matching the domain's own Functional Requirements where one exists.

Domain-prefixed naming is used consistently — not entity-prefixed — because the Domain is the single organizing taxonomy used everywhere else in this Foundation (folder structure, Domain Model, PRD structure). A permission for publishing an Announcement is `communication.publish_announcement`, not `announcement.publish`, because Announcement is an entity owned by the Communication domain, not a domain in its own right.

---

# Permission Scope

Two scopes exist, and every permission belongs to exactly one:

## Occasion-Scoped

Granted through an `OccasionMember` record (see ADR-002, ADR-009). Applies only within one Occasion. This is the default and covers almost every permission in this catalog.

## Platform-Scoped

Granted to a platform Administrator, independent of any single Occasion (Admin Portal). Used for cross-Occasion operations: user management, vendor approval, platform-wide reporting.

---

# Catalog

## Occasion

| Permission | Description | Scope |
| --- | --- | --- |
| `occasion.create` | Create a new Occasion | Platform (any authenticated user) |
| `occasion.edit` | Update Occasion details | Occasion |
| `occasion.manage_settings` | Change Occasion settings and visibility | Occasion |
| `occasion.archive` | Archive a completed Occasion | Occasion |
| `occasion.cancel` | Cancel an Occasion before completion | Occasion |
| `occasion.transfer_ownership` | Transfer Host ownership to another member | Occasion |
| `occasion.view` | View Occasion details | Occasion |

## People

| Permission | Description | Scope |
| --- | --- | --- |
| `people.invite_member` | Invite a User to join the Occasion | Occasion |
| `people.remove_member` | Remove an OccasionMember | Occasion |
| `people.assign_responsibility` | Assign a responsibility to an OccasionMember | Occasion |
| `people.manage_permissions` | Change an OccasionMember's permissions | Occasion |
| `people.view_members` | View the Occasion's member list | Occasion |

## Planning

| Permission | Description | Scope |
| --- | --- | --- |
| `planning.create_task` | Create a Task | Occasion |
| `planning.edit_task` | Edit a Task | Occasion |
| `planning.assign_task` | Assign a Task to an OccasionMember | Occasion |
| `planning.complete_task` | Mark a Task complete | Occasion |
| `planning.reopen_task` | Reopen a completed Task | Occasion |
| `planning.manage_checklist` | Create or edit a Checklist | Occasion |
| `planning.manage_milestone` | Create or edit a Milestone | Occasion |
| `planning.manage_timeline` | Schedule Timeline events | Occasion |

## Finance

| Permission | Description | Scope |
| --- | --- | --- |
| `finance.view_budget` | View the Budget and its categories | Occasion |
| `finance.edit_budget` | Create or edit the Budget and Budget Items | Occasion |
| `finance.record_pledge` | Record a Pledge | Occasion |
| `finance.record_contribution` | Record a received Contribution | Occasion |
| `finance.record_expense` | Record an Expense | Occasion |
| `finance.export_report` | Export financial reports | Occasion |

## Marketplace

| Permission | Description | Scope |
| --- | --- | --- |
| `marketplace.manage_vendor_profile` | Create or edit a Vendor's business profile | Platform (Vendor owner) |
| `marketplace.publish_service` | Publish or edit a Service | Platform (Vendor owner) |
| `marketplace.manage_inventory` | Manage Rental Item inventory | Platform (Vendor owner) |
| `marketplace.manage_availability` | Update a Vendor's availability calendar | Platform (Vendor owner) |
| `marketplace.request_quotation` | Request a Quotation from a Vendor | Occasion (Host) |
| `marketplace.submit_quotation` | Submit a Quotation | Platform (Vendor owner) |
| `marketplace.confirm_booking` | Confirm a Booking | Occasion (Host) / Platform (Vendor) |
| `marketplace.leave_review` | Leave a Review on a completed Booking | Occasion (verified customer) |
| `marketplace.respond_review` | Respond to a Review (future) | Platform (Vendor owner) |

## Communication

| Permission | Description | Scope |
| --- | --- | --- |
| `communication.publish_announcement` | Publish an Announcement | Occasion |
| `communication.schedule_reminder` | Configure a Reminder Rule | Occasion |
| `communication.view_restricted` | View restricted communications | Occasion |
| `communication.manage_preferences` | Manage own notification channel preferences | Self |

## Media

| Permission | Description | Scope |
| --- | --- | --- |
| `media.upload` | Upload a Media Asset | Occasion |
| `media.edit_metadata` | Edit a Media Asset's metadata | Occasion |
| `media.delete` | Delete a Media Asset | Occasion |
| `media.download` | Download a Media Asset | Occasion |
| `media.share` | Change a Media Asset's visibility/sharing | Occasion |

## Insights

| Permission | Description | Scope |
| --- | --- | --- |
| `insights.view_dashboard` | View the Readiness/Financial/Participation dashboards | Occasion |
| `insights.view_report` | View historical reports | Occasion |
| `insights.export_report` | Export a report | Occasion |

## Identity

| Permission | Description | Scope |
| --- | --- | --- |
| `identity.manage_own_profile` | Edit own profile information | Self |
| `identity.manage_own_sessions` | View or revoke own active sessions | Self |

## Platform Administration

Not Occasion-scoped. Granted only to platform Administrators (Admin Portal, see the MVP Definition).

| Permission | Description |
| --- | --- |
| `admin.manage_users` | Manage user accounts platform-wide |
| `admin.manage_occasions` | View/manage any Occasion for support or compliance purposes |
| `admin.approve_vendor` | Approve a Vendor application (Release 1.1) |
| `admin.view_reports` | View platform-wide reports |
| `admin.view_audit_logs` | View audit logs |

---

# Relationship to Domain PRDs

Each domain PRD's "Permissions" or "Security" section remains the *narrative* explanation of who can do what and why. This catalog is the *implementation* — the exact string that gets checked in code and API responses. If a domain PRD is updated to add a new capability, this catalog must be updated in the same change; a Functional Requirement is not considered fully specified until its permission exists here.

Broad umbrella phrases used informally elsewhere in the Foundation (for example, People PRD's illustrative "Manage Finance" example) are not enforceable permissions — the enforceable form is always the specific entries in this catalog (`finance.edit_budget`, `finance.record_contribution`, etc.).

---

# Related Documents

* Business Rules — BR-039 (authorization depends on Occasion context, not global roles)
* Security Standards — Default Deny (ADR-015)
* Domain Model
* People PRD
