# Zfs Btrfs

## Context & Problem
This topic explains how advanced filesystems change snapshotting, layering, and storage management. In production, this matters because advanced features usually solve a real boundary problem while introducing new operational cost.

## First Principles
- Advanced features are usually trade-offs, not universal upgrades.
- Stronger isolation, different filesystems, and rootless operation all change what the host must provide.
- If you cannot name the operational cost, you are not ready to adopt the feature.

## Production Implementation
Adopt the advanced feature only after you can state the requirement it solves and the host assumptions it introduces. Advanced settings pay for themselves only when the default path is measurably inadequate.

## Troubleshooting Approach
Advanced features fail at host boundaries first. Verify kernel support, filesystem compatibility, UID or GID mapping, runtime-handler configuration, and boot or virtualization prerequisites before debugging the application.

## Evolution & Alternatives
These topics reflect the industry's attempt to get better isolation, better portability, or better density without giving up too much convenience. Every option improves one boundary by making another boundary more complex.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- List the host prerequisites before you enable the feature so you can separate missing support from workload bugs.
- Compare the feature with the default path on isolation, portability, and operational complexity.
- Prove one concrete benefit and one new operational cost before deciding the feature is worth it.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [EFI Secure Boot](../07-efi-secure-boot/README.md).
