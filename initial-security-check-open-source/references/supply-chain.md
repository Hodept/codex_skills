# Supply Chain

Use this reference when source control, dependency, build, artifact, provenance, or release trust is in scope. Treat OpenSSF Scorecard and SLSA-style concepts as public review lenses, not organization policy or release approval criteria.

## OpenSSF Scorecard lenses

- Branch protection and required review for sensitive branches.
- CI tests, security checks, and maintained build automation.
- Dangerous workflow patterns, excessive token permissions, and untrusted pull request execution.
- Dependency update posture, pinned dependencies, lockfiles, and dependency source changes.
- Maintained project signals, known vulnerabilities, binary artifacts, fuzzing, code review, and signed releases where relevant.

## SLSA-style provenance concepts

- Provenance: a verifiable record of what source, builder, dependencies, parameters, and process produced an artifact.
- Integrity: protection against unauthorized changes to source, build steps, dependencies, artifacts, and release metadata.
- Isolation: separation between source review, build execution, artifact storage, deployment identity, and runtime permissions.
- Verification: consumers or deployment systems check signatures, provenance, digest pins, or other integrity metadata before use.
- Traceability: artifacts can be connected back to repository, commit, build, workflow, and release evidence.

## When to cite

- Cite OpenSSF Scorecard when reviewing repository hygiene, branch protection, CI/CD permissions, dependency hygiene, token permissions, or risky workflow patterns.
- Cite SLSA-style provenance when reviewing artifact integrity, build trust, signing, attestation, provenance, or source-to-deploy traceability.
- Do not assert supply-chain compromise from hygiene gaps alone; separate confirmed observations from possible risk.
- Pair with `references/secure-development.md` for SDLC practice context and `references/infrastructure-runtime.md` when deployment or runtime trust boundaries are affected.
