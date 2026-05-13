# Secure Development

Use this reference when a review needs NIST SP 800-218 Secure Software Development Framework context. Cite SSDF practice groups as public secure-development practice context only; do not convert them into organization-specific approval gates, severity, release status, or compliance claims.

## SSDF practice groups

- Prepare the Organization: define roles, security requirements, tooling, criteria, and development environment expectations before and during software work.
- Protect the Software: protect code, repositories, credentials, build systems, artifacts, release integrity, and development infrastructure from unauthorized access or tampering.
- Produce Well-Secured Software: design, implement, review, test, and document software to reduce security defects and unsafe behavior.
- Respond to Vulnerabilities: identify, track, analyze, remediate, disclose, and learn from vulnerabilities after discovery.

## When to cite

- Cite SSDF when reviewing SDLC controls, secure design, implementation practice, code review, testing, release readiness, vulnerability response, or development-environment controls.
- Use SSDF to frame questions such as whether roles, checks, artifact protection, vulnerability response, and release practices are visible or unknown.
- Do not state that a project meets SSDF unless a dedicated assessment verifies the relevant practices.
- Pair with `references/scm-cicd-review.md` for repository, build, and deployment changes, and with `references/secure-project-planning.md` for early workstream planning.
