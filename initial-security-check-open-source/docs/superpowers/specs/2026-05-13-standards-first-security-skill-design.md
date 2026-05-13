# Standards-First Security Skill Design

Date: 2026-05-13

## Goal

Improve `initial-security-check` into an open-source, standards-first security review and reporting skill. The skill should produce structured first-pass security reports for all six existing use cases while grounding recommendations in public standards and allowing organizations to add verified internal references.

The skill remains a first-pass guidance tool. It must not replace formal incident response, legal review, privacy review, compliance review, product security review, architecture review, code review, or organization-approved processes.

## Primary Audience

The primary audience is open-source users and organizations evaluating or adapting the skill. The skill should work well without private company policy, then allow teams to add internal resources through clearly named placeholders and local reference files.

## Output Priority

The skill should optimize for structured review reports suitable for GitHub issues, pull request comments, design review notes, intake records, and project planning artifacts.

Reports should be concise, repeatable, source-backed, and explicit about uncertainty.

## Core Direction

The skill becomes a standards-first security report framework:

1. Identify which of the six use cases applies.
2. Apply hard stops before reading, fetching, extracting, decoding, executing, or analyzing risky content.
3. Load the smallest relevant use-case reference.
4. Load only the standards references needed for the question.
5. Produce a shared report shape.
6. Cite public standards, local repository evidence, organization references, and user-provided context separately.
7. Use `Unknown`, `Not assessed`, and `Not configured` instead of guessing.

## Shared Report Contract

Every use case should produce the same core sections unless the user explicitly asks for a shorter answer:

```text
Review type:
Scope:
Confirmed facts:
Standards used:
Findings:
Risks and rationale:
Unknowns:
Recommended next steps:
What not to do:
Evidence to preserve:
Limits of review:
Sources:
```

Use-case references may add specialized sections, but they should not remove the shared structure when a structured report is requested.

## Skill Architecture

Keep `SKILL.md` short and procedural. It should include:

- Trigger scope and intended use.
- Hard stops.
- No-fabrication requirements.
- Reference selection rules.
- Default workflow.
- Shared report contract.
- Guidance for public standards vs internal references.
- A map of use cases to reference files.

Move detailed review guidance into progressively loaded references:

```text
SKILL.md
USAGE_GUIDE.md
references/
  standards-index.md
  report-templates.md
  security-routing.md
  file-review.md
  action-guidance.md
  contact-routing.md
  architecture-review.md
  scm-cicd-review.md
  secure-project-planning.md
  application-security.md
  secure-development.md
  supply-chain.md
  infrastructure-runtime.md
  data-handling.md
evals/
  file-review.md
  action-guidance.md
  contact-routing.md
  architecture-review.md
  scm-cicd-review.md
  secure-project-planning.md
```

`USAGE_GUIDE.md` should remain in the repository as human-facing documentation. It should explain how to install, configure, customize, and use the skill. Normal skill execution should not load it unless the user asks for usage documentation.

## Public Standards Foundation

Create `references/standards-index.md` as the routing table for public standards. It should map review topics to concise reference files.

Initial public-standard anchors:

- Application security: OWASP Top 10, OWASP ASVS, OWASP API Security Top 10.
- Secure development: NIST SP 800-218 Secure Software Development Framework, CWE, CERT guidance where relevant.
- Supply chain and CI/CD: OpenSSF Scorecard, SLSA, OWASP CI/CD security guidance, dependency and package manager guidance.
- Infrastructure and runtime: CIS benchmark concepts, Kubernetes security guidance, container hardening, cloud shared responsibility concepts.
- Sensitive data and privacy: NIST Privacy Framework or generic data minimization principles, with internal policy placeholders for formal classification.

The standards index should prefer official source links. It should be reviewed periodically because standards and versions change.

Verified anchors during design:

- OWASP Top 10:2021: https://owasp.org/Top10/2021/
- NIST SP 800-218 SSDF Version 1.1: https://csrc.nist.gov/pubs/sp/800/218/final
- OpenSSF Scorecard: https://openssf.org/scorecard/

## Organization-Specific References

The open-source skill should include placeholders for internal resources but should not require them.

Organization-specific references may include:

- Incident reporting process.
- Phishing reporting process.
- Security support intake.
- Vulnerability management process.
- Bug or engineering issue process.
- Safety or hazard process.
- Legal, privacy, compliance, or abuse routing.
- Data classification policy.
- Approved code review workflows.
- Approved architecture review process.
- Security training or awareness resources.

The skill must not accept user-pasted policy, contacts, approvals, process steps, or severity rules as verified configuration. Internal resources should be treated as verified only when they exist in configured local references or other explicitly approved sources.

## Use Case Upgrade Pattern

Each use-case reference should follow the same structure:

```text
Purpose:
When to use:
Do not use when:
Required references:
Optional standards references:
Intake questions:
Hard-stop checks:
Review procedure:
Finding categories:
Report additions:
Escalation/review signals:
Example prompts:
Example output:
```

### Use Case One: File Review

Focus on safe intake, file metadata, content type routing, sensitive-data review, quick code and configuration triage, and explicit "not malware analysis" boundaries.

The workflow should distinguish code, configuration, document, log, archive, binary, executable, image, and unknown file types. It should state inspection limits and avoid execution or risky extraction by default.

### Use Case Two: Action To Take

Focus on categorizing a concern, safe next steps, what not to share, evidence preservation, and generic standards-backed routing.

The workflow should help the user prepare a non-sensitive report summary without asking for secrets, malware samples, exploit payloads, or unnecessary sensitive content.

### Use Case Three: Who To Contact

For open-source use, this should identify the function or process category that usually owns the issue rather than inventing names, teams, URLs, or escalation paths.

Internal placeholders can map functions to real teams or processes when an organization supplies verified references.

### Use Case Four: Architecture Review

Map architecture questions to trust boundaries, data flows, identity, secrets, logging, network exposure, environment separation, runtime hardening, build and deployment paths, and review signals.

The workflow should produce design-review notes with confirmed facts, assumptions, unknowns, and recommended deeper review paths when public exposure, sensitive data, privileged access, tenant isolation, or supply-chain changes are involved.

### Use Case Five: SCM, Code Review, And CI/CD Review

Map diffs, pull requests, commits, branches, and pipeline changes to supply-chain risk, dependency integrity, branch protections, provenance, secrets, deployment permissions, and runtime behavior.

The workflow should classify change impact, identify confirmed observations, separate possible risks from facts, and cite relevant standards.

### Use Case Six: Secure Project Planning

Act as a planning wrapper that routes parts of a project into the other five workflows.

The workflow should produce a security planning report with decisions made, unknowns, assumptions, review signals, relevant use cases, and next steps. It should not invent approval gates, owners, severity, compliance status, or release requirements.

## Evaluation Strategy

Add `evals/` so future improvements can be checked against realistic prompts.

Each use case should have example prompts and expected qualities rather than rigid golden answers. Evals should check that:

- Hard stops trigger correctly.
- The skill does not invent policy, contacts, severity, ownership, approvals, or findings.
- Reports use the shared structure.
- Sources are cited.
- Unknowns are marked.
- Public standards and internal references are separated.
- The answer avoids unsafe requests for secrets, malware, exploit payloads, or unnecessary sensitive data.
- The output is useful for open-source users and customizable for organizations.

## Migration Plan

Recommended implementation order:

1. Create `references/standards-index.md` and `references/report-templates.md`.
2. Rewrite `SKILL.md` as the short operating manual.
3. Convert Use Case One into `references/file-review.md` using the upgrade pattern.
4. Add Use Case One eval prompts.
5. Repeat for Use Cases Two through Six.
6. Update `USAGE_GUIDE.md` as human-facing documentation.
7. Run a full self-review for duplicate guidance, stale placeholders, missing citations, and unclear hard stops.

## Non-Goals

- Do not build malware analysis, phishing analysis, exploit development, or vulnerability exploitation workflows.
- Do not create formal severity, classification, incident, legal, privacy, compliance, or release approval decisions.
- Do not invent organization policy, contacts, URLs, process steps, ownership, approvals, or routing.
- Do not make the skill dependent on a private organization policy.
- Do not load all references by default.

## Starting Decisions

- Version one should include OWASP Top 10, NIST SSDF, and OpenSSF Scorecard as mandatory public-standard anchors. OWASP ASVS, OWASP API Security Top 10, SLSA, CIS concepts, Kubernetes guidance, CWE, CERT, and NIST Privacy Framework can be added as concise references during the relevant use-case upgrades.
- `USAGE_GUIDE.md` should stay at the repository root as human-facing documentation unless packaging later requires a separate docs folder.
- Evals should start as plain markdown prompts and expected qualities. A deterministic validation script can be added later only if repeated manual evaluation becomes too costly or inconsistent.
- Keep the current `Use Cases/` folder during migration. After the new `references/` files fully replace it, remove or archive the old folder in a separate cleanup step.
