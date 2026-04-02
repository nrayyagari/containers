# Advanced

## What This Module Covers
This module covers the places where default container behavior stops being enough: rootless operation, cgroups v2, alternate filesystems, sandboxed runtimes, microVMs, and host trust assumptions.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-rootless-mode](./01-rootless-mode/README.md): how rootless execution changes privilege, storage, and networking behavior.
- [02-user-namespaces](./02-user-namespaces/README.md): how user namespaces underpin stronger isolation and rootless patterns.
- [03-cgroups-v2](./03-cgroups-v2/README.md): what the unified cgroup hierarchy changes for operators.
- [04-fuse-overlayfs](./04-fuse-overlayfs/README.md): why rootless and constrained setups use FUSE-backed overlay storage.
- [05-image-distribution](./05-image-distribution/README.md): how advanced distribution patterns improve speed, trust, or air-gapped operation.
- [06-zfs-btrfs](./06-zfs-btrfs/README.md): how advanced filesystems change snapshotting and storage management.
- [07-efi-secure-boot](./07-efi-secure-boot/README.md): how boot-time trust affects host integrity for container platforms.
- [08-gvisor-katata](./08-gvisor-katata/README.md): how sandboxed runtimes trade performance for stronger isolation.
- [09-firecracker-microvm](./09-firecracker-microvm/README.md): how microVMs bridge the gap between containers and VMs.
- [10-uds-uds](./10-uds-uds/README.md): how Unix domain sockets support local low-overhead service communication.

## Move On When
- You can meet this module's main goal: Adopt advanced features only when you can name the problem they solve and the cost they add.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Migration to Kubernetes](../14-migration-to-k8s/README.md).
