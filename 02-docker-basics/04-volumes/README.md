# Volumes

## What It Is
Volumes covers How Docker keeps data outside the container writable layer.

## Why It Matters
It matters because most day-to-day Docker mistakes are object-lifecycle mistakes.

## Key Points
- Image layers, writable layers, and persistent volumes have different lifecycles.
- Copy-on-write behavior affects both performance and troubleshooting.
- Durability depends on where data is stored, not on whether the write succeeded once.

## Lab Focus
Use the lab to prove how Docker keeps data outside the container writable layer.
- Key commands:
  - `docker volume create vol-lab`
  - `docker run --rm -v vol-lab:/data alpine:3.20 sh -c "echo persisted > /data/value.txt"`
  - `docker run --rm -v vol-lab:/data alpine:3.20 cat /data/value.txt`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Mixing up image content, writable-layer content, and durable data.
- Testing writes without proving what survives a restart.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Networking Basics](../05-networking-basics/README.md).
