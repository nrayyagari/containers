# Fundamentals

## What This Module Covers
This module explains the Linux mechanisms behind containers: namespaces, cgroups, layered filesystems, process model, and security boundaries. If this layer is fuzzy, later Docker and Kubernetes topics turn into command memorization instead of understanding.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-virtualization-basics](./01-virtualization-basics/README.md) | [Lab](./01-virtualization-basics/LAB.md): how virtualization evolved from hypervisors to OS-level isolation.
- [02-linux-namespaces](./02-linux-namespaces/README.md) | [Lab](./02-linux-namespaces/LAB.md): how processes get isolated views of PIDs, mounts, networks, IPC, UTS, and users.
- [03-control-groups-cgroups](./03-control-groups-cgroups/README.md) | [Lab](./03-control-groups-cgroups/LAB.md): how Linux enforces CPU, memory, and I/O limits.
- [04-union-filesystems](./04-union-filesystems/README.md) | [Lab](./04-union-filesystems/LAB.md): how layered filesystems build container roots from read-only image layers.
- [05-process-isolation](./05-process-isolation/README.md) | [Lab](./05-process-isolation/LAB.md): why a container is still a host process.
- [06-kernel-features](./06-kernel-features/README.md) | [Lab](./06-kernel-features/LAB.md): which Linux kernel features containers depend on.
- [07-container-vs-vm](./07-container-vs-vm/README.md) | [Lab](./07-container-vs-vm/LAB.md): where containers and VMs differ in isolation and overhead.
- [08-linux-capabilities](./08-linux-capabilities/README.md) | [Lab](./08-linux-capabilities/LAB.md): how root privileges are split into smaller permission sets.
- [09-seccomp-apparmor](./09-seccomp-apparmor/README.md) | [Lab](./09-seccomp-apparmor/LAB.md): how syscall filtering and MAC reduce kernel attack surface.
- [10-namespaces-deep-dive](./10-namespaces-deep-dive/README.md) | [Lab](./10-namespaces-deep-dive/LAB.md): how each namespace type behaves and where boundaries can leak.
- [11-cgroups-deep-dive](./11-cgroups-deep-dive/README.md) | [Lab](./11-cgroups-deep-dive/LAB.md): how controllers and pressure signals behave under load.
- [12-isolation-summary](./12-isolation-summary/README.md) | [Lab](./12-isolation-summary/LAB.md): how these primitives combine into a container boundary.

## Move On When
- You can meet this module's main goal: Explain container behavior in kernel terms, not just tool terms.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Docker Basics](../02-docker-basics/README.md).
