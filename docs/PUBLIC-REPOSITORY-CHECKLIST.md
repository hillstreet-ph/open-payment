# Public Repository Checklist

Run this checklist before changing repository visibility or publishing a release.

## Secrets and credentials

- No API keys, access tokens, passwords, private keys, OAuth secrets, cookies, or OTPs.
- No committed `.env` files or production configuration.
- Git history has been checked, not only the current branch.
- GitHub Actions uses encrypted secrets and restricted permissions.

## Private business information

- No real salary, internal cost, profit margin, banking, invoice, or payment evidence.
- No client-private agreements, conversations, identity records, or contact lists.
- No private Notion, Drive, storage, or signed-download links.
- Examples use synthetic data.

## Application security

- Tenant isolation is enforced server-side and at the database layer.
- Client views use explicit allowlists of fields.
- Logs and error reports redact sensitive values.
- Uploads are private by default and validated.
- Administrative and payment actions require explicit authorization and audit events.

## Repository governance

- README accurately states the current maturity.
- LICENSE is intentional.
- SECURITY.md provides a private reporting route before production.
- Branch protection and required checks are enabled.
- Secret scanning and dependency alerts are enabled where available.
- CODEOWNERS and review requirements protect sensitive paths.

## Final verification

After publication, verify visibility from a signed-out session and immediately review the repository, releases, Actions logs, issues, pull requests, branches, tags, and commit history for unintended disclosure.
