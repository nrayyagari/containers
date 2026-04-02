# Kernel Features

## What It Is
Kernel Features covers Which Linux kernel features containers depend on.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- Containers depend on kernel primitives that already existed before modern container tooling.
- Namespaces isolate view, cgroups control resources, and security features reduce privilege.
- Runtimes assemble these pieces, but the kernel still enforces them.

## Lab Focus
Use the lab to prove which Linux kernel features containers depend on.
- Key commands:
  - `docker run -d --name fnd-lab alpine:3.20 sleep 300`
  - `docker inspect fnd-lab --format "{{.State.Pid}} {{.State.Status}}"`
  - `docker exec fnd-lab cat /proc/1/status | sed -n '1,25p'`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Containers vs Virtual Machines](../07-container-vs-vm/README.md).
