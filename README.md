# Open Payment

Open Payment is the finance and payment-operations service for the HillStreet / KobePlay ecosystem. It is intended to manage expense requests, subscription and payroll approvals, payment records, invoice references, budget reporting, and auditable approval workflows without exposing private operator costs or credentials to client-facing portals.

> Project status: planning and foundation. Interfaces, schemas, and deployment components may change until the first stable release.

## Goals

- Centralize payment and finance workflows.
- Separate private operations data from client-visible summaries.
- Require human approval for sensitive or high-impact actions.
- Maintain an auditable history of requests, decisions, and status changes.
- Integrate safely with Open Connect, Notion, storage, and deployment services.

## Access boundaries

| Area | Intended audience | Examples |
|---|---|---|
| Private operations | Owner and explicitly authorized finance administrators | Actual costs, salaries, credentials, invoices, internal margins |
| Internal team | Authorized operations staff | Assigned requests, approved operating budgets, task status |
| Client portal | Approved client viewers | Client-facing charges, approval requests, sanitized summaries |
| Public repository | Everyone | Source code, public architecture, setup guidance, security policy |

Private costs, payroll data, banking records, identity documents, API keys, passwords, tokens, production environment files, and raw invoices must never be committed.

## Planned workflow

1. A finance or payment request is created.
2. Policy checks classify its sensitivity and required approvers.
3. Authorized reviewers approve, reject, or request changes.
4. Execution occurs through an approved payment provider or manual process.
5. A sanitized status is published to the correct portal.
6. Audit events and evidence references are retained in protected storage.

## Planned architecture

- **Web/API layer:** finance requests, approvals, reporting, and integrations
- **Database:** tenant-scoped operational records and audit history
- **Identity:** role-based access with organization and workspace boundaries
- **Storage:** protected invoice and evidence objects; metadata only in public code
- **Integrations:** Open Connect, Notion, Supabase, Cloudflare, Sentry, and a portable container runtime
- **Observability:** structured logs, error monitoring, health checks, and audit events

See [Architecture](docs/ARCHITECTURE.md) and the [Public Repository Checklist](docs/PUBLIC-REPOSITORY-CHECKLIST.md).

## Development status

This repository does not yet claim production readiness. Before production use it needs:

- an approved functional specification and threat model;
- database schema and row-level access policies;
- authentication and authorization tests;
- provider integrations using server-side secrets;
- CI, dependency review, secret scanning, and security checks;
- backup and restore procedures;
- deployment, rollback, monitoring, and incident runbooks.

## Security

Use environment variables or an approved secret manager for runtime credentials. Commit only safe examples such as `.env.example` with placeholder values. Report vulnerabilities privately to the maintainers; do not open a public issue containing exploit details or sensitive data.

## License

No license has been selected yet. Until a license file is added, copyright remains with the repository owner and no reuse rights are granted automatically.
