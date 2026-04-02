# Migration to Kubernetes

## What This Module Covers
This module explains what actually changes during a Kubernetes migration: pods, CRI-native runtimes, rollout control, cluster networking, configuration delivery, storage, and observability. The point is to break Docker-era assumptions before they cause migration bugs.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-docker-to-containerd](./01-docker-to-containerd/README.md) | [Lab](./01-docker-to-containerd/LAB.md): why Kubernetes nodes moved from Docker-centric plumbing to CRI-native runtimes.
- [02-cri-compatibility](./02-cri-compatibility/README.md) | [Lab](./02-cri-compatibility/LAB.md): what runtime compatibility kubelet expects from a node.
- [03-image-format](./03-image-format/README.md) | [Lab](./03-image-format/LAB.md): how OCI image compatibility affects migration success.
- [04-pod-concept](./04-pod-concept/README.md) | [Lab](./04-pod-concept/LAB.md): why a Pod is a scheduling and lifecycle unit, not just grouped containers.
- [05-deployment-strategies](./05-deployment-strategies/README.md) | [Lab](./05-deployment-strategies/LAB.md): how rollout strategy changes migration risk.
- [06-config-secrets](./06-config-secrets/README.md) | [Lab](./06-config-secrets/LAB.md): how Kubernetes separates config and secret delivery from the image.
- [07-networking-changes](./07-networking-changes/README.md) | [Lab](./07-networking-changes/LAB.md): how service exposure, DNS, and network policy change in Kubernetes.
- [08-storage-migration](./08-storage-migration/README.md) | [Lab](./08-storage-migration/LAB.md): how persistent data semantics change under scheduling.
- [09-service-mesh](./09-service-mesh/README.md) | [Lab](./09-service-mesh/LAB.md): what a service mesh adds and what complexity it introduces.
- [10-monitoring-observability](./10-monitoring-observability/README.md) | [Lab](./10-monitoring-observability/LAB.md): how Kubernetes changes what you observe and where you collect it.

## Move On When
- You can meet this module's main goal: Translate the operating model, not just the syntax.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.
