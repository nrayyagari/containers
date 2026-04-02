# 14 Migration to Kubernetes: Security-Aware Transition Path

## Context & Problem
Migrating from standalone containers to Kubernetes changes runtime, networking, identity, policy, and operations. Teams fail migrations when they map Docker-only mental models directly to Kubernetes.

## First Principles
Kubernetes adds control-plane mediated execution. Runtime decisions, service discovery, storage, rollout safety, and security posture are policy-driven rather than host-local defaults.

## Production Implementation
- Standardize runtime tooling around CRI-aware commands.
- Use immutable artifacts and digest pinning.
- Separate config from secrets.
- Adopt safe rollout and rollback patterns.
- Build migration observability before cutover.

## Troubleshooting Approach
Trace failures by layer: runtime -> pod/workload -> service/network -> storage -> policy -> observability.

## Evolution & Alternatives
This path reflects modern Kubernetes operations after dockershim removal and widespread policy-first platform engineering.

## Next Steps
Use `DATADOG-K8S-SECURITY-STUDY.md` with `repos/kubernetes` security/networking modules for deeper practice.

## Topic Map
- [01-docker-to-containerd](./01-docker-to-containerd/README.md) | [Lab](./01-docker-to-containerd/LAB.md)
- [02-cri-compatibility](./02-cri-compatibility/README.md) | [Lab](./02-cri-compatibility/LAB.md)
- [03-image-format](./03-image-format/README.md) | [Lab](./03-image-format/LAB.md)
- [04-pod-concept](./04-pod-concept/README.md) | [Lab](./04-pod-concept/LAB.md)
- [05-deployment-strategies](./05-deployment-strategies/README.md) | [Lab](./05-deployment-strategies/LAB.md)
- [06-config-secrets](./06-config-secrets/README.md) | [Lab](./06-config-secrets/LAB.md)
- [07-networking-changes](./07-networking-changes/README.md) | [Lab](./07-networking-changes/LAB.md)
- [08-storage-migration](./08-storage-migration/README.md) | [Lab](./08-storage-migration/LAB.md)
- [09-service-mesh](./09-service-mesh/README.md) | [Lab](./09-service-mesh/LAB.md)
- [10-monitoring-observability](./10-monitoring-observability/README.md) | [Lab](./10-monitoring-observability/LAB.md)

## Zero-Confusion Summary
- What it is:
  - A practical migration module from container-only operations to Kubernetes-native operations.
- What it is not:
  - It is not a full Kubernetes curriculum by itself.
- When to use:
  - Use when preparing workloads and teams for production Kubernetes migration.
- When not to use:
  - Do not treat this as optional if your platform moves to Kubernetes.
