# Storage Driver

## What It Is
Storage Driver covers How copy-on-write storage drivers back Docker layers.

## Why It Matters
It matters because most day-to-day Docker mistakes are object-lifecycle mistakes.

## Key Points
- Image layers, writable layers, and persistent volumes have different lifecycles.
- Copy-on-write behavior affects both performance and troubleshooting.
- Durability depends on where data is stored, not on whether the write succeeded once.

## Lab Focus
Use the lab to prove how copy-on-write storage drivers back Docker layers.
- Key commands:
  - `docker pull alpine:3.20`
  - `docker run -d --name dk-lab alpine:3.20 sleep 300`
  - `docker inspect dk-lab --format "{{.Config.Image}} {{.State.Status}}"`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Mixing up image content, writable-layer content, and durable data.
- Testing writes without proving what survives a restart.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Compose YAML](../10-compose-yaml/README.md).
