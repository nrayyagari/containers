# Inode Management

## What It Is
Inode Management covers How inode exhaustion breaks containers even when disk space remains.

## Why It Matters
It matters because state bugs usually surface late and are expensive to recover from.

## Key Points
- Image layers, writable layers, and persistent volumes have different lifecycles.
- Copy-on-write behavior affects both performance and troubleshooting.
- Durability depends on where data is stored, not on whether the write succeeded once.

## Practice Check
- Write a small file, restart the container, and confirm whether the data survived for the reason you expected.
- Use `docker inspect`, `mount`, `df`, or `df -i` to prove what backend is actually in use.

## Common Mistakes
- Mixing up image content, writable-layer content, and durable data.
- Testing writes without proving what survives a restart.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Backup Restore](../10-backup-restore/README.md).
