# Fundamentals

## Context & Problem
Linux kernel isolation primitives behind containers.

## First Principles
Namespaces isolate visibility, cgroups isolate resources, and privilege controls reduce blast radius.

## Production Implementation
Collect kernel-level evidence before changing policies or runtime settings.

## Troubleshooting Approach
Trace symptom to namespace, cgroup, capability, or syscall boundary.

## Evolution & Alternatives
Containers evolved from process isolation primitives, while VMs provide hardware-level isolation with more overhead.

## Next Steps
Proceed to Docker basics to connect kernel primitives with day-2 operations.

## Topic Map
- [01-virtualization-basics](./01-virtualization-basics/README.md) | [Lab](./01-virtualization-basics/LAB.md)
- [02-linux-namespaces](./02-linux-namespaces/README.md) | [Lab](./02-linux-namespaces/LAB.md)
- [03-control-groups-cgroups](./03-control-groups-cgroups/README.md) | [Lab](./03-control-groups-cgroups/LAB.md)
- [04-union-filesystems](./04-union-filesystems/README.md) | [Lab](./04-union-filesystems/LAB.md)
- [05-process-isolation](./05-process-isolation/README.md) | [Lab](./05-process-isolation/LAB.md)
- [06-kernel-features](./06-kernel-features/README.md) | [Lab](./06-kernel-features/LAB.md)
- [07-container-vs-vm](./07-container-vs-vm/README.md) | [Lab](./07-container-vs-vm/LAB.md)
- [08-linux-capabilities](./08-linux-capabilities/README.md) | [Lab](./08-linux-capabilities/LAB.md)
- [09-seccomp-apparmor](./09-seccomp-apparmor/README.md) | [Lab](./09-seccomp-apparmor/LAB.md)
- [10-namespaces-deep-dive](./10-namespaces-deep-dive/README.md) | [Lab](./10-namespaces-deep-dive/LAB.md)
- [11-cgroups-deep-dive](./11-cgroups-deep-dive/README.md) | [Lab](./11-cgroups-deep-dive/LAB.md)
- [12-isolation-summary](./12-isolation-summary/README.md) | [Lab](./12-isolation-summary/LAB.md)

## Zero-Confusion Summary
- Read topic README first.
- Run LAB step-by-step in order.
- Mark lab complete only when Verify and Answer Key pass criteria are satisfied.
