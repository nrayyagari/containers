# Advanced

## Context & Problem
Default container behaviors are enough until a security boundary, portability target, performance profile, or platform restriction forces you deeper. These topics exist for the moments when basic Docker knowledge is no longer enough to make a safe decision.

## First Principles
Advanced container features usually trade simplicity for stronger isolation, different host assumptions, or better density. That means you must be explicit about what problem you are solving, because the operational cost is usually higher than the default path.

## Production Implementation
Use advanced features because a requirement demands them, not because they sound modern. Stronger isolation, alternate filesystems, rootless modes, and microVMs all come with new operational edges.

## Troubleshooting Approach
Advanced failures often sit at boundaries between subsystems: kernel feature availability, filesystem compatibility, user mapping, runtime handler support, or host boot trust. When defaults stop working, verify the host assumptions first.

## Evolution & Alternatives
Many of these topics represent the industry's answer to two competing forces: wanting VM-like isolation with container-like speed and wanting rootless portability without giving up practical usability.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-rootless-mode](./01-rootless-mode/README.md): how rootless execution changes privilege, storage, and networking behavior.
- [02-user-namespaces](./02-user-namespaces/README.md): how user namespaces underpin advanced isolation and rootless patterns.
- [03-cgroups-v2](./03-cgroups-v2/README.md): what the unified cgroup hierarchy changes for operators.
- [04-fuse-overlayfs](./04-fuse-overlayfs/README.md): why rootless and constrained environments use FUSE-backed overlay storage.
- [05-image-distribution](./05-image-distribution/README.md): how advanced image distribution patterns improve speed, trust, and air-gapped operations.
- [06-zfs-btrfs](./06-zfs-btrfs/README.md): how advanced filesystems change snapshotting, layering, and storage management.
- [07-efi-secure-boot](./07-efi-secure-boot/README.md): how boot-time trust influences host integrity for container platforms.
- [08-gvisor-katata](./08-gvisor-katata/README.md): how sandboxed runtimes trade performance for stronger isolation.
- [09-firecracker-microvm](./09-firecracker-microvm/README.md): how microVMs bridge the gap between containers and traditional virtual machines.
- [10-uds-uds](./10-uds-uds/README.md): how Unix domain sockets support local, secure, low-overhead service communication.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After this module, revisit the migration and runtime sections with a sharper eye for trade-offs. Advanced options are only useful when you can explain what operational pain they remove and what new cost they introduce.
Continue with [Migration to Kubernetes](../14-migration-to-k8s/README.md) when the topic map in this module feels operationally clear.
