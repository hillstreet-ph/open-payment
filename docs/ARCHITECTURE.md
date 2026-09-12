# Open Payment Architecture

## Scope

Open Payment is the finance-control component for payment requests, approvals, expense tracking, subscription and payroll summaries, and client-safe reporting. It must not become a credential vault, a bank-account datastore, or a public archive of invoices.

## Trust zones

### Public code

Contains application source, schemas without real records, safe configuration examples, documentation, tests, and deployment templates.

### Private operations

Contains actual costs, salaries, margins, invoice evidence, internal vendor accounts, and administrative decisions. Access is owner-controlled and denied by default.

### Client portal

Contains only explicitly approved client-facing charges, request status, summaries, and evidence that has been sanitized for client access.

### External providers

Payment, identity, storage, database, email, and monitoring services are accessed through server-side integrations. Credentials remain in an approved secret manager and are never returned to browsers or committed to Git.

## Core domain model

- Organization and workspace
- User, role, and policy
- Vendor and subscription
- Payment or expense request
- Approval step and decision
- Invoice/evidence reference
- Budget category and reporting period
- Audit event
- Client-visible sanitized summary

## Authorization principles

- Deny access by default.
- Enforce organization and workspace tenancy at the database layer.
- Separate owner, finance administrator, staff, client approver, and read-only viewer roles.
- Never derive client visibility only from UI filtering.
- Require step-up or human approval for credential, payout, bank, payroll, and permission changes.
- Record immutable audit events for material state transitions.

## Data handling

Store sensitive files in protected object storage. Database rows should reference protected objects and include classification, owner, retention, and access-policy metadata. Logs must redact credentials, financial identifiers, private URLs, and personal data.

## Deployment target

The planned portable deployment supports GitHub-based CI/CD, Cloudflare at the edge, Supabase for database/auth/storage, Sentry for error monitoring, and Zeabur or another compatible container runtime. Production selection remains subject to implementation review.

## Release gates

A production release requires automated tests, secret scanning, dependency review, authorization tests, database migration review, backup/restore validation, rollback documentation, monitoring, and an explicit human approval.
