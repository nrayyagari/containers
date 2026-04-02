# Docker vs containerd

## What It Is
Docker vs containerd covers How Docker and containerd differ in scope and operational role.

## Why It Matters
It matters because runtime failures are hard to fix when you inspect the wrong layer.

## Key Points
- Runtime stacks are layered and each layer has a different job.
- High-level managers handle images and lifecycle; low-level runtimes create the process.
- Use tools that match the layer that owns the workload.

## Lab Focus
Use the lab to prove how Docker and containerd differ in scope and operational role.
- Key commands:
  - `systemctl status containerd --no-pager || true`
  - `crictl info || true`
  - `crictl ps -a || true`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Collapsing several runtime layers into 'Docker is broken'.
- Using the wrong CLI for the layer that owns the workload.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Low Level Runtime](../06-low-level-runtime/README.md).
