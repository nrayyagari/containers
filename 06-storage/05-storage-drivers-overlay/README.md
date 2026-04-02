# Storage Drivers Overlay

## Context & Problem
This topic explains how overlay-based storage drivers implement writable layers. In production, this matters because state problems are expensive to recover from and often only show up after restarts, migrations, or outages.

## First Principles
- Container storage has multiple lifecycles: image layers, writable layers, volumes, and external storage backends.
- Copy-on-write and overlay behavior can change both performance and the meaning of a write operation.
- Durability depends on where data lives, not on whether the application wrote it successfully once.

## Production Implementation
Choose the storage mechanism based on data ownership and recovery requirements, not on which mount syntax is easiest to remember. Practice proving where the data really lives before you trust a backup or cleanup step.

## Troubleshooting Approach
Ask three questions early: where does the data live, who owns it, and what path exposes it to the process? That separates permission problems from backend problems and durability problems from simple path mistakes.

## Evolution & Alternatives
Container storage practices matured as teams learned that writable layers are not a data strategy. Durable systems moved toward explicit volume ownership, backend choice, and recovery planning.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Identify which path is image content, writable-layer content, and durable content before you test anything.
- Use `docker inspect`, `mount`, `df`, or `df -i` to prove what backend and capacity the workload is actually using.
- Practice a small write-and-restart cycle so you can prove which data survives and why.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [NFS Volumes](../06-nfs-volumes/README.md).
