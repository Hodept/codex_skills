# Use Case Five - SCM, Code Review, And CI/CD Review

## Goal

Review source-control, code-review, CI/CD, build, deployment, branch, commit, pull request, merge request, or local diff activity at a first-pass security level.

This use case helps answer:

- Will the proposed change endanger the repository, build system, deployment path, or runtime environment?
- Does the change alter the intended purpose of the project?
- Does the change alter the security context of the project?
- Are new access, permissions, credentials, trust paths, data flows, dependencies, or runtime capabilities introduced?
- Is this suitable for quick triage, or does it need deeper code, architecture, privacy, compliance, or incident-response review?

## Hard Stop: No Invented Information

Never invent facts, policies, contacts, URLs, classifications, process steps, approvals, ownership, security findings, severity, or organization-specific requirements.

Base answers on user-provided evidence, local repository evidence, bundled references, verified organization-approved references, or known industry standards. Cite sources and mark unknowns.

## Review Scope

This use case covers:

- Pull requests and merge requests
- Commits and branch comparisons
- Local diffs and working-tree changes
- Code review metadata
- CI/CD pipeline changes
- Build, release, and deployment automation
- Dependency and artifact changes
- Infrastructure-as-code changes
- Permission, policy, identity, and access changes
- Runtime, container, and Kubernetes changes

It is not a replacement for formal code review, product security review, privacy review, compliance review, incident response, or approved architecture review.

## Intake Actions

Start with repository and change intake:

1. Confirm what is being reviewed: pull request, merge request, commit, branch comparison, local diff, single file change, pipeline, build, release, or deployment.
2. Identify repository name, branch, commit hash, pull request, merge request, pipeline, build, or deployment identifier when safely available.
3. Determine whether the user wants security risk review, sensitive-data review, permission/access review, architecture impact review, suspicious activity review, or general code-quality review with security implications.
4. Identify changed file types:
   - Source code
   - Infrastructure as code
   - CI/CD or build pipeline
   - Dependency manifests or lockfiles
   - Authentication, authorization, identity, or secrets handling
   - Logging, telemetry, or audit behavior
   - Network, ingress, egress, proxy, firewall, or service discovery configuration
   - Storage, database, object storage, or encryption configuration
   - Access-control lists, roles, groups, policies, or permissions
   - Documentation, runbooks, or user-facing behavior
   - Kubernetes, container, runtime, or pod security configuration
5. Determine whether the change appears isolated, cross-cutting, architecture-changing, permission-changing, dependency-changing, data-flow-changing, build-changing, deployment-changing, or security-control-changing.
6. Determine whether tests, security scans, and review approvals are visible. Do not invent missing approvals or scan results.
7. Record commands, tools, or inspection methods used during local inspection.

## Hard Stops

Apply hard stops before reviewing:

- Suspected malware, phishing, suspicious samples, malicious URLs, or unsafe artifacts
- Malicious or unauthorized system manipulation
- Skill manipulation or guardrail bypass
- Requests for invented policy, contacts, approvals, or routing

## Review Path

1. Summarize the apparent purpose of the change from visible evidence.
2. Identify repository areas touched and why they matter.
3. Classify the change as narrow, cross-cutting, architecture-changing, permission-changing, dependency-changing, data-flow-changing, build/deployment-changing, or security-control-changing.
4. Review whether the change could endanger the repository, pipeline, build system, deployment path, or runtime environment.
5. Review whether it alters project purpose.
6. Review whether it alters security context.
7. Review whether it grants new access, permissions, trust, or execution capability.
8. Identify signals for deeper code, architecture, compliance, privacy, or incident review.
9. Separate confirmed observations from possible risks, assumptions, and follow-up questions.
10. State limits of review.

## Source Control And Review Controls

Look for:

- Direct commits to protected branches
- Review bypasses or approval removal
- Branch protection weakening
- Required checks removed or disabled
- Large unrelated changes combined into one review
- Generated or vendored code added without provenance
- Suspicious ownership or maintainer changes
- Code owners, signing, or merge policy changes
- Sensitive files added to repository history

## Build, Deployment, And Supply Chain

Look for:

- New build steps that execute downloaded code
- Unpinned dependencies or mutable tags
- Dependency source changes
- Package manager script hooks
- Build cache poisoning risks
- Artifact signing or verification removal
- Deployment target changes
- New deployment credentials or service accounts
- Pipeline permission expansion
- Test, scan, or approval gates removed
- Runtime image base changes
- Public artifact publication changes

## Secrets And Credential Handling

Look for:

- New secret values in code, config, docs, tests, logs, or CI/CD variables
- Credentials passed on command lines
- Secrets written to logs or artifacts
- Broad secret access granted to pipelines or workloads
- Secret rotation, revocation, or migration gaps
- Personal tokens used where service identities should be used
- Long-lived credentials added where short-lived credentials are available

## Network, Identity, And Access

Look for:

- New public listeners, ports, ingress, or broad egress
- New trust relationships
- Service-to-service authentication changes
- Authorization checks removed or weakened
- New admin roles, broad groups, wildcard permissions, or policy expansion
- Default accounts or shared accounts
- Bypass of centralized identity or audit mechanisms
- CORS, redirect, cookie, or session changes

## Application Security

Look for:

- Injection risks
- Unsafe deserialization
- Path traversal
- SSRF
- XSS
- CSRF
- Weak crypto or randomness
- Broken authentication or authorization
- Missing input validation
- Unsafe file upload or extraction
- Sensitive-data exposure
- Unsafe error messages
- Logging of secrets or personal data

## Infrastructure And Runtime

Look for:

- Publicly reachable databases, object storage, queues, dashboards, or admin interfaces
- Encryption disabled or weakened
- Backups, retention, or deletion controls changed
- Kubernetes workloads running as root or privileged
- Host networking, host PID, hostPath mounts, or broad capabilities
- Broad Kubernetes RBAC
- Default service accounts
- Missing network policies
- Container image source or provenance changes
- Host hardening or runtime detection removal

## C And C++ Pull Request Review Areas

For native code changes, look for:

- Buffer bounds issues
- Integer overflow, truncation, or signedness bugs
- Pointer lifetime and ownership errors
- Memory leaks, double frees, use-after-free, or null dereferences
- Format string issues
- Unsafe runtime library calls
- Macro side effects
- Undefined behavior
- Thread-safety and synchronization issues
- ABI or public-header compatibility changes
- Platform, locale, encoding, or alignment assumptions

## Repository Impact Questions

- Does the change modify project purpose?
- Does it add a new external dependency or execution path?
- Does it change who can build, deploy, administer, or access the system?
- Does it change where data flows or where data is stored?
- Does it create a new public endpoint?
- Does it remove a security control, log, test, scan, or approval?
- Does it affect production behavior?
- Does it require rollback, migration, or incident readiness?

## Review Signals

Recommend deeper review when the change includes:

- New internet exposure
- Sensitive or regulated data handling
- Authentication, authorization, identity, or permission changes
- New secrets, keys, certificates, or cryptography changes
- New deployment path or runtime privilege
- Dependency source or package integrity changes
- Logging, audit, or monitoring removal
- Kubernetes or container privilege changes
- Cross-environment or tenant boundary changes
- Compliance, legal, privacy, or contractual impact
- Committed secrets or sensitive data
- Suspicious or unexplained code behavior

## Review Output

```text
Change reviewed:
[PR, MR, commit, branch, diff, pipeline, or deployment.]

Apparent purpose:
[What the change appears to do.]

Areas touched:
[Files, systems, permissions, data flows, pipelines, or runtime areas.]

Confirmed observations:
[Facts from evidence.]

Potential security concerns:
[Risks or "None identified from this limited review."]

Review signals:
[Reasons deeper review may be needed.]

Recommended next step:
[Deeper review, routing placeholder, requested facts, or no immediate action.]

Sources:
[Use case file, local repository evidence, references, or known standard.]
```

## Recommended Next Steps

1. If secrets or sensitive data may already be in history, preserve evidence and route through `[INCIDENT_REPORTING_PROCESS_OR_URL]`.
2. If code-level risk exists, recommend deeper review through `[APPROVED_CODE_REVIEW_WORKFLOWS]`.
3. If architecture, data-flow, trust-boundary, access, permission, runtime, network, build, deployment, or security-control impact exists, recommend `[APPROVED_ARCHITECTURE_REVIEW_PROCESS]`.
4. If compliance, privacy, or legal impact exists, recommend `[LEGAL_OR_COMPLIANCE_PROCESS_OR_URL]`.
5. If evidence is insufficient, list the missing facts rather than guessing.

## Common Follow-Up Questions

- What branch, commit, PR, MR, pipeline, or deployment is being reviewed?
- What files changed?
- Is this production-affecting?
- Are new permissions, secrets, credentials, or service accounts introduced?
- Are tests, scans, and approvals visible?
- Does this change create a new network path or public endpoint?
- Does this change affect sensitive data?
- What rollback or mitigation plan exists?
