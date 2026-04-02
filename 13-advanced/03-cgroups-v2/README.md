# cgroups v2

## Context & Problem
This topic explains what the unified cgroup hierarchy changes for operators. In production, this matters because advanced features usually solve a real boundary problem while introducing new operational cost.
A cgroup does not make a workload efficient. It only organizes and constrains what the kernel will allow that workload to consume.

## First Principles
- cgroups organize processes into a hierarchy and apply controller-specific rules to those groups.
- Resource problems show up as measurable kernel behavior such as throttling, reclaim pressure, or OOM kills.
- If you only look at the application, you will miss the host-level control that actually constrained it.

## Production Implementation
Adopt the advanced feature only after you can state the requirement it solves and the host assumptions it introduces. Advanced settings pay for themselves only when the default path is measurably inadequate.

## Troubleshooting Approach
Separate application inefficiency from kernel enforcement. Check for throttling, reclaim pressure, and OOM evidence before changing limits or blaming the scheduler.

## Evolution & Alternatives
These topics reflect the industry's attempt to get better isolation, better portability, or better density without giving up too much convenience. Every option improves one boundary by making another boundary more complex.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- List the host prerequisites before you enable the feature so you can separate missing support from workload bugs.
- Compare the feature with the default path on isolation, portability, and operational complexity.
- Prove one concrete benefit and one new operational cost before deciding the feature is worth it.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Fuse Overlayfs](../04-fuse-overlayfs/README.md).
