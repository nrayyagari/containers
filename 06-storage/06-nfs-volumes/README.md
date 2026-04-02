# NFS Volumes

## What It Is
NFS Volumes covers How network filesystems enable shared data across hosts.

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
Then continue to [Volume Permissions](../07-volume-permissions/README.md).
