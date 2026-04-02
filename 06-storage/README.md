# Storage

## Context & Problem
Containers make it easy to ignore data until an outage, a restart, or a migration proves that state was attached to the wrong place. Storage mistakes are among the most expensive mistakes in container platforms because they turn into data loss or corrupt recovery procedures.

## First Principles
A container filesystem is not where durable application state should casually live. You need to know what belongs in the image, what belongs in the writable layer, what belongs in a volume, and what belongs in an external storage system.

## Production Implementation
Choose storage based on lifecycle and ownership, not convenience. The right question is not 'How do I mount this?' but 'Who owns this data, how long must it live, and how will I recover it under pressure?'

## Troubleshooting Approach
Separate filesystem layering issues from persistent-volume issues and host-disk issues. A container can fail because of permission mismatch, inode exhaustion, overlay copy-up behavior, backend latency, or backup mistakes, and those are different classes of incidents.

## Evolution & Alternatives
Early container workloads leaned on host paths and writable layers. Mature environments moved toward named volumes, plugin-backed storage, network filesystems, snapshots, and explicit backup practices because state must survive host and scheduler churn.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-bind-mounts](./01-bind-mounts/README.md): how host paths are mounted directly into containers.
- [02-named-volumes](./02-named-volumes/README.md): how Docker-managed volumes persist data independent of containers.
- [03-tmpfs-mounts](./03-tmpfs-mounts/README.md): how in-memory mounts trade durability for speed and cleanliness.
- [04-volume-drivers](./04-volume-drivers/README.md): how external plugins extend Docker volume backends.
- [05-storage-drivers-overlay](./05-storage-drivers-overlay/README.md): how overlay-based storage drivers implement writable layers.
- [06-nfs-volumes](./06-nfs-volumes/README.md): how network filesystems enable shared data across hosts.
- [07-volume-permissions](./07-volume-permissions/README.md): how UID, GID, and mode bits determine whether containerized processes can read and write data.
- [08-persistence-strategies](./08-persistence-strategies/README.md): how to separate ephemeral state from data that must survive restarts or rescheduling.
- [09-inode-management](./09-inode-management/README.md): how inode exhaustion breaks containers even when disk space looks available.
- [10-backup-restore](./10-backup-restore/README.md): how to protect and restore container data without corrupting live workloads.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After storage, continue into security. Together, storage and security define what a compromised or misconfigured container can change and how far that damage can spread.
Continue with [Security](../07-security/README.md) when the topic map in this module feels operationally clear.
