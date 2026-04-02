# Containers vs Virtual Machines

## What It Is
Containers share the host kernel and isolate process context. Virtual machines virtualize a full machine boundary, including a guest kernel.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- Containers and VMs solve isolation with different boundaries.
- VMs package a guest kernel; containers share the host kernel.
- That difference drives trade-offs in startup time, density, and default isolation strength.

## Lab Focus
Use the lab to prove where containers and VMs differ in isolation and overhead.
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
Then continue to [Linux Capabilities](../08-linux-capabilities/README.md).
