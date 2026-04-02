# Container Runtimes

## What This Module Covers
This module explains who actually launches a container and how kubelet, CRI, containerd, shims, and low-level runtimes fit together. It exists so runtime failures can be debugged at the right layer.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-runc](./01-runc/README.md) | [Lab](./01-runc/LAB.md): how the low-level OCI runtime creates the container process.
- [02-containerd](./02-containerd/README.md) | [Lab](./02-containerd/LAB.md): how containerd manages images, snapshots, tasks, and runtime integration.
- [03-cri](./03-cri/README.md) | [Lab](./03-cri/LAB.md): how kubelet talks to runtimes through the Container Runtime Interface.
- [04-crio](./04-crio/README.md) | [Lab](./04-crio/LAB.md): how CRI-O provides a Kubernetes-focused runtime implementation.
- [05-docker-vs-containerd](./05-docker-vs-containerd/README.md) | [Lab](./05-docker-vs-containerd/LAB.md): how Docker and containerd differ in scope and operational role.
- [06-low-level-runtime](./06-low-level-runtime/README.md) | [Lab](./06-low-level-runtime/LAB.md): what low-level runtimes do versus higher-level managers.
- [07-high-level-runtime](./07-high-level-runtime/README.md) | [Lab](./07-high-level-runtime/LAB.md): what higher-level runtimes add around lifecycle and image management.
- [08-shim-process](./08-shim-process/README.md) | [Lab](./08-shim-process/LAB.md): why shims sit between the runtime manager and individual containers.
- [09-oci-spec](./09-oci-spec/README.md) | [Lab](./09-oci-spec/LAB.md): how OCI specs standardize image and runtime behavior.
- [10-runtime-classes](./10-runtime-classes/README.md) | [Lab](./10-runtime-classes/LAB.md): how Kubernetes selects different runtime handlers per workload.

## Move On When
- You can meet this module's main goal: Know which runtime layer is authoritative for the workload you are debugging.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Networking](../05-networking/README.md).
