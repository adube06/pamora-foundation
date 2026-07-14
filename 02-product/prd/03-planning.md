# Planning Domain PRD

**Version:** 1.0.0

**Status:** Approved

**Stability:** Frozen (see [Stability Within a Domain PRD](../01-prd.md#stability-within-a-domain-prd))

---

# 1. Purpose

The Planning Domain coordinates all work required to successfully complete an Occasion.

It transforms a high-level idea into an executable plan by organizing tasks, milestones, timelines, and responsibilities.

This domain is responsible for execution management.

---

# 2. Business Goals

Enable every Occasion to be planned in a structured and collaborative way.

The platform should answer:

* What needs to be done?
* Who is responsible?
* When is it due?
* What is blocking progress?
* How close are we to readiness?

---

# 3. Scope

The Planning Domain owns:

* Tasks
* Checklists
* Milestones
* Timeline
* Dependencies
* Calendar Events
* Planning Templates (Future)

It does **not** own:

* Participants (People)
* Budgets (Finance)
* Vendor Services (Marketplace)
* Notifications (Communication)

---

# 4. Core Entities

## Task

Represents a unit of work.

Attributes:

* Title
* Description
* Status
* Priority
* Due Date
* Assignee
* Labels
* Attachments
* Completion Date

---

## Checklist

A collection of related Tasks.

Examples:

* Catering
* Decorations
* Transportation
* Invitations
* Ceremony
* Reception

---

## Milestone

Represents a significant planning objective.

Examples:

* Venue Confirmed
* Invitations Sent
* Budget Approved
* Vendors Confirmed
* Ceremony Ready

Milestones summarize progress rather than replacing Tasks.

---

## Timeline Event

Represents a dated activity.

Examples:

* Committee Meeting
* Vendor Visit
* Dress Fitting
* Funeral Service
* Reception

---

# 5. Task Lifecycle

```text
Draft
  │
  ▼
Open
  │
  ▼
In Progress
  │
  ▼
Completed
```

Alternative transitions:

```text
Open
 │
 ├── Cancelled
 └── Deferred
```

Rules:

* Every state transition creates an activity entry.
* Completed Tasks become read-only unless reopened by an authorized user.

---

# 6. Functional Requirements

## FR-001 — Create Task

Priority: Critical

Authorized users shall create Tasks within an Occasion.

Acceptance Criteria:

* Task belongs to one Occasion.
* Creator recorded.
* Activity logged.

---

## FR-002 — Assign Task

A Task may be assigned to one Occasion Member.

Future releases may support multiple assignees.

---

## FR-003 — Update Task Status

Authorized members may update Task status.

Progress updates should appear immediately within the Occasion workspace.

---

## FR-004 — Create Checklist

Users may organize related Tasks into Checklists.

---

## FR-005 — Create Milestone

Milestones summarize important planning achievements.

Milestones may depend on completion of multiple Tasks.

---

## FR-006 — Timeline Management

Planning activities may be scheduled on the Occasion timeline.

---

## FR-007 — Reopen Task

Authorized users may reopen completed Tasks.

All reopen actions must be logged.

---

# 7. Priorities

Supported priorities:

* Critical
* High
* Medium
* Low

Priority affects:

* Dashboard ordering
* Notifications
* Readiness calculations

---

# 8. Dependencies

Tasks may depend on other Tasks.

Example:

```text
Book Venue
      │
      ▼
Pay Deposit
      │
      ▼
Decorate Venue
```

A blocked Task should clearly indicate which dependency is preventing progress.

---

# 9. Templates (Future)

Planning Templates allow reusable planning structures.

Examples:

* Wedding Template
* Funeral Template
* Birthday Template

Templates generate default Checklists, Milestones, and Tasks for new Occasions.

---

# 10. Domain Events

The Planning Domain emits events such as:

* TaskCreated
* TaskAssigned
* TaskStarted
* TaskCompleted
* TaskReopened
* ChecklistCreated
* MilestoneCompleted

Other domains may subscribe to these events where appropriate.

---

# 11. Integrations

People Domain

* Assignees
* Responsibilities

Finance Domain

* Budget-related Tasks

Marketplace Domain

* Vendor-related Tasks

Communication Domain

* Reminders
* Notifications

Insights Domain

* Readiness calculations
* Progress dashboards

---

# 12. Security

Permissions include:

* Create Tasks
* Edit Tasks
* Assign Tasks
* Complete Tasks
* Manage Checklists
* Manage Milestones

Permission decisions are based on Occasion Membership.

---

# 13. Reporting

Metrics include:

* Total Tasks
* Completed Tasks
* Overdue Tasks
* Completion Rate
* Milestones Achieved
* Average Completion Time

---

# 14. Success Metrics

Planning succeeds when:

* Responsibilities are clear.
* Deadlines are met.
* Bottlenecks are visible.
* Readiness improves over time.

---

# 15. Future Enhancements

Potential additions:

* Recurring Tasks
* AI-generated Planning Plans
* Automatic Deadline Suggestions
* Calendar Synchronization
* Workload Balancing
* Smart Dependency Detection

---

# Architecture Note — Planning Hierarchy (ADR-003)

Most "event apps" treat an occasion as `date + invitation`. In reality:

> **Occasion = Hundreds of small coordinated decisions.**

This is why the Planning Domain is the execution engine of Pamora.

A Task alone is not enough. The Planning Domain must have this hierarchy:

```text
Occasion
    │
    ▼
Planning
    │
    ├── Milestones
    │
    ├── Checklists
    │
    ├── Tasks
    │
    └── Timeline
```

This has several advantages:

* Milestone shows the big step (e.g. Venue Confirmed).
* Checklist groups related work together (e.g. Decorations).
* Task is the actual unit of execution.
* Timeline shows when things happen.

This is the difference between a "to-do list" app and an Occasion Operating System. When someone opens the Occasion Workspace, they should see real progress on the event, not just an unstructured long list of tasks. See [ADR-003](../../06-decisions/ADR-003-planning-hierarchy.md).

---

# Related Documents

* Occasion PRD
* People PRD
* Finance PRD
* Business Rules
* User Journeys
* Insights PRD
