# Identity Domain PRD

**Version:** 1.0.0

**Status:** Approved

**Stability:** Frozen (see [Stability Within a Domain PRD](../01-prd.md#stability-within-a-domain-prd))

---

# 1. Purpose

The Identity Domain manages user identity, authentication, account security, and profile management.

It provides a trusted identity layer for all Pamora experiences while remaining independent from business participation.

The Identity Domain does not determine what a user may do within an Occasion. That responsibility belongs to the People Domain.

Identity and People are often confused, but in Pamora's architecture they must remain completely separate:

* **Identity** = Who is this user?
* **People** = What does this user do inside an Occasion?

Separating these domains keeps the system easy to extend toward Organization Workspace, Vendor Workspace, and future integrations.

---

# 2. Business Goals

Enable users to:

* Create and secure an account.
* Sign in safely.
* Verify identity.
* Manage personal profile information.
* Control account security settings.

---

# 3. Scope

The Identity Domain owns:

* User Account
* Authentication
* Profile
* Email Verification
* Phone Verification
* Password Management
* Session Management
* Multi-Factor Authentication (Future)

It does **not** own:

* Occasion Membership
* Permissions
* Responsibilities
* Invitations
* Vendor Services

---

# 4. Core Entities

## User

Represents a unique individual using Pamora.

Required attributes:

* User ID
* Full Name
* Email (optional depending on region)
* Phone Number
* Preferred Language
* Time Zone
* Profile Photo
* Account Status

---

## Authentication Method

Supported methods:

* Email + Password
* Phone + OTP
* Google (Future)
* Apple (Future)

Additional providers may be introduced without affecting business domains.

---

## Session

Represents an authenticated user session.

Attributes include:

* Device
* Login Time
* Last Activity
* IP Address (where appropriate)
* Expiration Time

---

# 5. Functional Requirements

## FR-001 — Register Account

Users shall be able to create an account using supported authentication methods.

Acceptance Criteria:

* Identity created.
* Verification initiated where required.
* Audit log generated.

---

## FR-002 — Sign In

Users shall authenticate using a supported authentication method.

Successful authentication creates a new active session.

---

## FR-003 — Verify Contact Information

Users may verify:

* Email
* Phone Number

Verification status must be visible within the profile.

---

## FR-004 — Reset Password

Users shall securely reset their password.

Password reset tokens must expire automatically.

---

## FR-005 — Manage Profile

Users may update personal information without affecting business records.

---

## FR-006 — Manage Sessions

Users may:

* View active sessions.
* Revoke sessions.
* Sign out from all devices.

---

# 6. Account Status

Supported statuses:

* Pending Verification
* Active
* Suspended
* Locked
* Closed

Status changes must be audited.

---

# 7. Security

Identity security requirements include:

* Password hashing
* Session expiration
* Brute-force protection
* Secure token generation
* Verification workflows
* Audit logging

Future enhancements:

* Multi-Factor Authentication (MFA)
* Passkeys
* Trusted devices

---

# 8. Domain Events

The Identity Domain emits:

* UserRegistered
* UserVerified
* UserSignedIn
* UserSignedOut
* PasswordResetRequested
* PasswordChanged
* SessionRevoked

Business domains may subscribe to these events where appropriate.

---

# 9. Integrations

People Domain

* User identity for Occasion Membership

Marketplace Domain

* Vendor owner identity

Communication Domain

* Verified delivery channels

Insights Domain

* Account statistics

---

# 10. Privacy

Personally identifiable information (PII) must be protected.

Access to user profile information must follow least-privilege principles.

Identity data should not be duplicated across business domains.

---

# 11. Reporting

Metrics include:

* Registered Users
* Active Users
* Verification Rate
* Login Success Rate
* Failed Login Attempts
* Active Sessions

---

# 12. Success Metrics

The Identity Domain succeeds when:

* Account creation is simple.
* Authentication is secure.
* Identity is trusted.
* Users can recover access safely.
* Business domains remain independent of authentication logic.

---

# 13. Future Enhancements

Potential capabilities:

* Single Sign-On (SSO)
* Enterprise Identity Providers
* Biometric Authentication
* Device Trust
* Identity Federation
* Account Recovery Options

---

# Architecture Note — Identity Is Separate from Membership (ADR-009)

This is a critical foundation decision.

Do not store roles or permissions on `users`.

Instead:

```text
User
   │
   ▼
Identity Domain
   │
   ▼
Occasion Membership (People Domain)
   │
   ▼
Permissions
```

Example:

* Amina has one Pamora account.
* She is Host on Wedding A.
* She is Guest on Funeral B.
* She is Treasurer on Graduation C.
* She is a Vendor Owner on Business D.

Her account stays the same. What changes is her membership and permissions within each workspace.

This makes the architecture ready for:

* Multi-workspace
* Multi-organization
* Vendor portal
* Enterprise edition

See [ADR-009](../../06-decisions/ADR-009-identity-separate-from-membership.md).

---

# Related Documents

* People PRD
* Communication PRD
* Business Rules
* Engineering Playbook
* Security Standards
