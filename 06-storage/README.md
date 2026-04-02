# Storage

## What This Module Covers
This module separates image content, writable-layer content, volumes, bind mounts, network storage, and backup strategy. It exists because container storage mistakes usually surface only after a restart, migration, or incident.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-bind-mounts](./01-bind-mounts/README.md): how host paths are mounted directly into containers.
- [02-named-volumes](./02-named-volumes/README.md): how Docker-managed volumes persist data independently of containers.
- [03-tmpfs-mounts](./03-tmpfs-mounts/README.md): how in-memory mounts trade durability for speed and cleanliness.
- [04-volume-drivers](./04-volume-drivers/README.md): how plugins extend Docker volume backends.
- [05-storage-drivers-overlay](./05-storage-drivers-overlay/README.md): how overlay-based storage drivers implement writable layers.
- [06-nfs-volumes](./06-nfs-volumes/README.md): how network filesystems enable shared data across hosts.
- [07-volume-permissions](./07-volume-permissions/README.md): how UID, GID, and mode bits affect container file access.
- [08-persistence-strategies](./08-persistence-strategies/README.md): how to separate ephemeral state from durable state.
- [09-inode-management](./09-inode-management/README.md): how inode exhaustion breaks containers even when disk space remains.
- [10-backup-restore](./10-backup-restore/README.md): how to protect and restore container data safely.

## Move On When
- You can meet this module's main goal: Know where the data really lives and what survives a restart.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Security](../07-security/README.md).
