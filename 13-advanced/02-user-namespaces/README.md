# User Namespaces

## Context & Problem
This topic explains how user namespaces underpin advanced isolation and rootless patterns. In production, this matters because advanced features usually solve a real boundary problem while introducing new operational cost.
A namespace is not a whole container by itself; it is one scoped view of one class of system resources.

## First Principles
- Namespaces change what a process can see, not what the host physically contains.
- Different namespace types isolate different resources: PID, network, mount, IPC, UTS, and user IDs.
- A convincing container boundary appears only when namespaces are combined with cgroups, a filesystem, and security policy.

## Production Implementation
Adopt the advanced feature only after you can state the requirement it solves and the host assumptions it introduces. Advanced settings pay for themselves only when the default path is measurably inadequate.

## Troubleshooting Approach
When isolation looks wrong, compare namespace links under `/proc/<pid>/ns` and decide which namespace is actually shared. Do not start with firewall or filesystem changes until you know the scope is correct.

## Evolution & Alternatives
These topics reflect the industry's attempt to get better isolation, better portability, or better density without giving up too much convenience. Every option improves one boundary by making another boundary more complex.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- List the host prerequisites before you enable the feature so you can separate missing support from workload bugs.
- Compare the feature with the default path on isolation, portability, and operational complexity.
- Prove one concrete benefit and one new operational cost before deciding the feature is worth it.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [cgroups v2](../03-cgroups-v2/README.md).
