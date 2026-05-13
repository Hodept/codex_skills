# Standards Index

Use this reference to choose the smallest relevant public-standard source for a first-pass security review. Prefer official sources and cite the specific standard used in the report.

## Required Anchors

| Topic | Primary source | Use when |
| --- | --- | --- |
| Web and application security | OWASP Top 10:2021 - https://owasp.org/Top10/2021/ | Reviewing common application risk categories such as access control, injection, cryptography, insecure design, vulnerable components, logging, SSRF, or security misconfiguration. |
| Secure software development | NIST SP 800-218 SSDF Version 1.1 - https://csrc.nist.gov/pubs/sp/800/218/final | Reviewing development practices, secure design, secure implementation, vulnerability response, or SDLC process questions. |
| Open-source supply chain posture | OpenSSF Scorecard - https://openssf.org/scorecard/ | Reviewing repository hygiene, branch protection, dependencies, token permissions, pinned dependencies, CI/CD posture, and supply-chain signals. |

## Optional Topic References

| Topic | Candidate sources | Use when |
| --- | --- | --- |
| Application verification depth | OWASP ASVS | A user needs deeper app-security verification categories beyond first-pass Top 10 triage. |
| API security | OWASP API Security Top 10 | The review concerns APIs, authorization, object-level access, rate limits, mass assignment, or API inventory. |
| Weakness taxonomy | CWE | The review needs a neutral weakness category without asserting exploitability or severity. |
| Native code | CERT C and CERT C++ guidance | The review concerns C, C++, native bindings, memory safety, integer behavior, or undefined behavior. |
| Supply-chain provenance | SLSA | The review concerns build provenance, artifact integrity, release integrity, or build pipeline trust. |
| Infrastructure and runtime | CIS benchmark concepts, Kubernetes security guidance, cloud shared responsibility docs | The review concerns infrastructure, Kubernetes, containers, cloud accounts, identity, network exposure, or runtime hardening. |
| Privacy and data minimization | NIST Privacy Framework or local data classification policy | The review concerns personal data, regulated data, privacy impact, or data minimization. |

## Source Rules

- Cite public standards separately from repository evidence and organization-specific references.
- Do not treat a public standard as an organization policy, approval gate, severity model, or compliance decision.
- Do not invent version numbers. If the exact version was not checked, cite the source name without a version.
- If an organization-specific reference is unavailable, say `Not configured`.
