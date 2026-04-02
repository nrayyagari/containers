# Fundamentals

## Context & Problem
Most container confusion starts here: people learn Docker commands before they understand what the Linux kernel is actually doing. This module explains the primitives that make containers possible so later topics stop feeling like magic.

## First Principles
A container is not a tiny virtual machine. It is a regular host process that gets an isolated view of some resources, controlled access to CPU and memory, a layered filesystem, and additional security restrictions. If you cannot name the kernel primitive behind a behavior, you do not yet understand the failure mode.

## Production Implementation
When something container-related breaks, start with kernel evidence before touching orchestration or application code. `/proc`, `/sys/fs/cgroup`, mount state, namespace links, and security policy usually tell the truth faster than a wrapper CLI.

## Troubleshooting Approach
Map the symptom to the correct boundary: visibility, resources, storage, or privilege. Then inspect the host-level object that enforces that boundary before changing runtime flags or application settings.

## Evolution & Alternatives
Containers grew out of long-lived Linux capabilities such as namespaces, cgroups, capabilities, and union filesystems. Modern tools like containerd and Kubernetes did not replace those primitives; they automated them.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-virtualization-basics](./01-virtualization-basics/README.md) | [Lab](./01-virtualization-basics/LAB.md): how virtualization evolved from hardware emulation and hypervisors to OS-level isolation.
- [02-linux-namespaces](./02-linux-namespaces/README.md) | [Lab](./02-linux-namespaces/LAB.md): how the kernel gives processes isolated views of PIDs, mounts, networks, IPC, UTS, and users.
- [03-control-groups-cgroups](./03-control-groups-cgroups/README.md) | [Lab](./03-control-groups-cgroups/LAB.md): how Linux enforces CPU, memory, and I/O boundaries on a group of processes.
- [04-union-filesystems](./04-union-filesystems/README.md) | [Lab](./04-union-filesystems/LAB.md): how layered filesystems build a writable container root from read-only image layers.
- [05-process-isolation](./05-process-isolation/README.md) | [Lab](./05-process-isolation/LAB.md): why a container is still a host process even when it feels like a separate machine.
- [06-kernel-features](./06-kernel-features/README.md) | [Lab](./06-kernel-features/LAB.md): which Linux kernel features containers rely on and what each one contributes.
- [07-container-vs-vm](./07-container-vs-vm/README.md) | [Lab](./07-container-vs-vm/LAB.md): where containers and virtual machines differ in kernel sharing, isolation, and overhead.
- [08-linux-capabilities](./08-linux-capabilities/README.md) | [Lab](./08-linux-capabilities/LAB.md): how root privileges are split into smaller permission sets.
- [09-seccomp-apparmor](./09-seccomp-apparmor/README.md) | [Lab](./09-seccomp-apparmor/LAB.md): how syscall filtering and mandatory access control reduce kernel attack surface.
- [10-namespaces-deep-dive](./10-namespaces-deep-dive/README.md) | [Lab](./10-namespaces-deep-dive/LAB.md): how each namespace type behaves, what it isolates, and where boundaries can still leak.
- [11-cgroups-deep-dive](./11-cgroups-deep-dive/README.md) | [Lab](./11-cgroups-deep-dive/LAB.md): how controllers, hierarchies, and pressure signals behave under load.
- [12-isolation-summary](./12-isolation-summary/README.md) | [Lab](./12-isolation-summary/LAB.md): how namespaces, cgroups, layered filesystems, and security policy combine into a container.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After this module, move to Docker Basics and connect the kernel model to the objects and commands engineers use every day.
Continue with [Docker Basics](../02-docker-basics/README.md) when the topic map in this module feels operationally clear.
