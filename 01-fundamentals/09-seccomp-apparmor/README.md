# Seccomp Apparmor

## What It Is
Seccomp Apparmor covers How syscall filtering and MAC reduce kernel attack surface.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- Container security is layered; no single flag makes a workload safe.
- Least privilege means reducing what the process can do and what you trust it with.
- A security control is only useful if you can explain what it blocks.

## Lab Focus
Use the lab to prove how syscall filtering and MAC reduce kernel attack surface.
- Key commands:
  - `docker run -d --name fnd-lab alpine:3.20 sleep 300`
  - `docker inspect fnd-lab --format "{{.State.Pid}} {{.State.Status}}"`
  - `docker exec fnd-lab cat /proc/1/status | sed -n '1,25p'`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Loosening every control at once instead of identifying the blocking layer.
- Treating scanning or signing as a substitute for runtime hardening.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Namespaces Deep Dive](../10-namespaces-deep-dive/README.md).
