# Union Filesystems

## What It Is
Union filesystems let multiple read-only layers and one writable layer appear as one filesystem tree. That is how image layers become a usable container root filesystem.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- Image layers, writable layers, and persistent volumes have different lifecycles.
- Copy-on-write behavior affects both performance and troubleshooting.
- Durability depends on where data is stored, not on whether the write succeeded once.

## Lab Focus
Use the lab to prove how layered filesystems build container roots from read-only image layers.
- Key commands:
  - `docker run -d --name fnd-lab alpine:3.20 sleep 300`
  - `docker inspect fnd-lab --format "{{.State.Pid}} {{.State.Status}}"`
  - `docker exec fnd-lab cat /proc/1/status | sed -n '1,25p'`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Mixing up image content, writable-layer content, and durable data.
- Testing writes without proving what survives a restart.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Process Isolation](../05-process-isolation/README.md).
