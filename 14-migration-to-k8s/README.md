# Migration To K8s

## Context & Problem
Practical migration path from container-only to Kubernetes-native operations.

## First Principles
Kubernetes introduces desired-state API, pod semantics, policy controls, and declarative rollout.

## Production Implementation
Migrate in waves with runtime, networking, storage, and observability validation gates.

## Troubleshooting Approach
Separate app defects from platform policy and control-plane failures.

## Evolution & Alternatives
Modern migrations use progressive rollout and policy guardrails over big-bang cutovers.

## Next Steps
Pair this with repositories under repos/kubernetes for deeper cluster controls.

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
- Read topic README first.
- Run LAB step-by-step in order.
- Mark lab complete only when Verify and Answer Key pass criteria are satisfied.
