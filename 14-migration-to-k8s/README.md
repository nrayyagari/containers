# Migration to Kubernetes

## Context & Problem
Teams often try to migrate by mapping Docker concepts one-to-one into Kubernetes. That leads to broken assumptions about runtimes, pods, networking, rollout behavior, storage, and observability. This module explains what actually changes so the migration is architectural rather than cosmetic.

## First Principles
Kubernetes is a control plane, not a bigger Docker host. Workloads become declarative objects, pods replace the single-container mental model, CRI replaces Docker-specific node plumbing, and storage plus networking become cluster concerns rather than host concerns.

## Production Implementation
Migrate by re-evaluating lifecycle, identity, state, and traffic flow for each workload. A successful migration proves that the platform model changed without breaking correctness, operability, or recovery procedures.

## Troubleshooting Approach
When migration problems appear, ask whether the failure comes from image assumptions, runtime compatibility, pod semantics, configuration delivery, service exposure, or monitoring gaps. 'It worked in Docker' is not a diagnosis.

## Evolution & Alternatives
Kubernetes dropped dockershim and standardized on CRI-native runtimes, while the ecosystem added stronger patterns for rollout, policy, and observability. Migration today is less about translating YAML and more about adopting the platform's operating model.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-docker-to-containerd](./01-docker-to-containerd/README.md) | [Lab](./01-docker-to-containerd/LAB.md): why Kubernetes nodes moved from Docker-centric plumbing to CRI-native runtimes.
- [02-cri-compatibility](./02-cri-compatibility/README.md) | [Lab](./02-cri-compatibility/LAB.md): what runtime compatibility requirements kubelet expects from a node.
- [03-image-format](./03-image-format/README.md) | [Lab](./03-image-format/LAB.md): how OCI image compatibility affects migration success.
- [04-pod-concept](./04-pod-concept/README.md) | [Lab](./04-pod-concept/LAB.md): why a Kubernetes Pod is a scheduling and lifecycle unit, not just grouped containers.
- [05-deployment-strategies](./05-deployment-strategies/README.md) | [Lab](./05-deployment-strategies/LAB.md): how rolling, blue or green, and canary rollouts change migration risk.
- [06-config-secrets](./06-config-secrets/README.md) | [Lab](./06-config-secrets/LAB.md): how Kubernetes separates configuration and secret delivery from the image.
- [07-networking-changes](./07-networking-changes/README.md) | [Lab](./07-networking-changes/LAB.md): how moving to Kubernetes changes service exposure, DNS, and network policy.
- [08-storage-migration](./08-storage-migration/README.md) | [Lab](./08-storage-migration/LAB.md): how persistent data semantics change when workloads become scheduled rather than host-pinned.
- [09-service-mesh](./09-service-mesh/README.md) | [Lab](./09-service-mesh/LAB.md): what a service mesh adds and what complexity it introduces.
- [10-monitoring-observability](./10-monitoring-observability/README.md) | [Lab](./10-monitoring-observability/LAB.md): how Kubernetes changes what you observe and where you collect it.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
This module is the bridge from standalone container literacy to Kubernetes-native reasoning. Pair it with your Kubernetes repo after you can clearly explain what a Pod, runtime, and control loop each contribute.
