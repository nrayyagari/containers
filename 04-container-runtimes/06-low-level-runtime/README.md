# Low Level Runtime

## What It Is
Low Level Runtime covers What low-level runtimes do versus higher-level managers.

## Why It Matters
It matters because runtime failures are hard to fix when you inspect the wrong layer.

## Key Points
- Runtime stacks are layered and each layer has a different job.
- High-level managers handle images and lifecycle; low-level runtimes create the process.
- Use tools that match the layer that owns the workload.

## Lab Focus
Use the lab to prove what low-level runtimes do versus higher-level managers.
- Key commands:
  - `ps -ef | grep -E "containerd|shim|runc" | grep -v grep | head -n 30`
  - `docker run -d --name rt-lab alpine:3.20 sleep 300`
  - `docker inspect rt-lab --format "{{.Id}} {{.State.Pid}}"`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Collapsing several runtime layers into 'Docker is broken'.
- Using the wrong CLI for the layer that owns the workload.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [High Level Runtime](../07-high-level-runtime/README.md).
