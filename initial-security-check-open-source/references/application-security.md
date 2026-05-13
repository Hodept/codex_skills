# Application Security

Use this reference when a first-pass review needs a concise application-security lens. Cite OWASP Top 10 categories as public risk context only; do not claim exploitability, severity, compliance status, or organization policy from OWASP alone.

## OWASP Top 10 categories

- A01 Broken Access Control: authorization bypass, insecure object access, missing server-side checks, privilege escalation, tenant isolation, CORS misconfiguration, or forced browsing.
- A02 Cryptographic Failures: weak or missing encryption, unsafe key handling, exposed secrets, insecure transport, weak randomness, or sensitive data sent or stored without protection.
- A03 Injection: SQL, NoSQL, OS command, LDAP, template, expression-language, or other untrusted input interpreted as commands or queries.
- A04 Insecure Design: missing threat modeling, unsafe trust boundaries, insecure workflows, weak abuse controls, or designs that rely on client-side enforcement.
- A05 Security Misconfiguration: default settings, unnecessary features, permissive headers, verbose errors, exposed admin interfaces, open cloud resources, or weak hardening.
- A06 Vulnerable and Outdated Components: outdated, unsupported, vulnerable, unmaintained, or untracked dependencies, images, libraries, frameworks, or runtimes.
- A07 Identification and Authentication Failures: weak login, session, MFA, credential recovery, password, token, or identity lifecycle controls.
- A08 Software and Data Integrity Failures: unsigned or unverified updates, untrusted plugins, unsafe CI/CD trust, insecure deserialization, or unverified artifacts.
- A09 Security Logging and Monitoring Failures: missing security events, unprotected logs, alerting gaps, or insufficient evidence for investigation.
- A10 Server-Side Request Forgery: user-controlled outbound requests, metadata service access, internal network probing, weak URL allowlisting, or proxy abuse paths.

## When to cite

- Cite OWASP Top 10 when visible evidence maps to a common web, API, application, authentication, authorization, data protection, logging, or component risk category.
- Use the category name to describe the review lens, not to assert a confirmed vulnerability unless the evidence supports it.
- Prefer OWASP API Security Top 10 or ASVS when the user needs API-specific or deeper verification categories.
- Pair with `references/data-handling.md`, `references/infrastructure-runtime.md`, or `references/supply-chain.md` when the app issue depends on data sensitivity, runtime exposure, or dependency/build trust.
