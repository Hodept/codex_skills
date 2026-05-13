# Data Handling

Use this reference when a review involves files, logs, application data, documents, datasets, telemetry, customer content, user content, or sharing decisions. It helps identify sensitive-data indicators without inventing formal classification.

## Sensitive-data indicators

- Credentials, API keys, tokens, passwords, private keys, signing keys, session cookies, OAuth material, or recovery codes.
- Personal, employee, customer, partner, child, health, financial, payment, government ID, biometric, location, or regulated data.
- Confidential business data, contracts, roadmaps, pricing, unreleased product information, source code, security designs, vulnerabilities, incident evidence, or internal investigations.
- Internal identifiers such as hostnames, IP addresses, account IDs, tenant IDs, repository names, stack traces, logs, alerts, tickets, architecture diagrams, or operational runbooks.
- Production data, backups, exports, debug dumps, crash dumps, database snapshots, object storage contents, or test data copied from production.

## Data minimization

- Ask for high-level summaries when raw sensitive content is not needed.
- Avoid requesting or repeating secrets, full tokens, full personal records, exploit payloads, suspected malware content, or unnecessary logs.
- Prefer narrow excerpts, redacted examples, metadata, counts, schemas, or field names when they answer the review question.
- Separate confirmed data indicators from unknowns and do not infer data categories beyond evidence.

## Sharing context

- Treat public posting, vendor sharing, third-party uploads, broad chat distribution, and external tickets as higher-risk sharing contexts.
- Note whether data is internal-only, externally shared, public, production-derived, customer-provided, employee-provided, regulated, or unknown.
- Preserve evidence guidance without expanding distribution of sensitive material.

## Internal classification behavior

- If a verified local classification policy exists, use it and cite it.
- If no verified local policy exists, describe observed indicators and state formal classification as `Not configured` or `Unknown`.
- Do not invent classification labels, approval requirements, handling tiers, severity, owners, or release status.
