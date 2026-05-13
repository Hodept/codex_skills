# Infrastructure And Runtime

Use this reference for first-pass review of cloud, network, container, Kubernetes, host, managed platform, deployment, and operational runtime security. It provides review prompts, not organization policy or approval criteria.

## Review lenses

- Environment separation: development, test, staging, production, disaster recovery, management, tenant, and data domains should have explicit boundaries and controlled trust paths.
- Network exposure: public ingress, private endpoints, egress, peering, gateways, proxies, firewalls, security groups, routing, and broad rules such as `0.0.0.0/0` should match intended exposure.
- Identity and access: users, services, workloads, pipelines, and operators should use distinct identities with least privilege, auditable authorization, and scoped delegation.
- Secrets and certificates: secrets, keys, certificates, tokens, and credentials should have secure generation, storage, scoped runtime access, rotation, revocation, and compromise handling.
- Kubernetes: clusters, namespaces, node pools, RBAC, service accounts, network policies, admission controls, image provenance, secrets, and workload placement should reflect trust boundaries.
- Containers: images should be maintained, provenance should be known, unnecessary privileges should be avoided, and workloads should not run as root, privileged, host network, host PID, or with broad capabilities unless justified and reviewed.
- Logging and monitoring: security-relevant events, admin actions, deployment actions, access decisions, and control failures should be logged without secrets or unnecessary sensitive data.
- Runtime hardening: patching, minimal services and ports, endpoint or runtime detection, configuration drift detection, file integrity, backup protection, and tamper-resistant audit evidence should be considered where relevant.

## Deeper review signals

- New internet exposure, broad ingress, broad egress, or public administrative interfaces.
- Cross-environment, cross-account, tenant, customer, or third-party trust paths.
- Privileged Kubernetes or container runtime behavior.
- New administrative access, break-glass path, shared account, local user, or bypass of central identity.
- New secrets, certificates, cryptographic providers, deployment credentials, or signing keys.
- Logging, audit, monitoring, backup, or retention gaps that affect investigation or recovery.
