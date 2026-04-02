# Virtualization Basics

## What It Is
Virtualization Basics covers How virtualization evolved from hypervisors to OS-level isolation.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- Hypervisors isolate at a machine boundary; containers isolate within one host kernel.
- Containers usually start faster and pack more densely because they do not boot a guest OS.
- The isolation trade-off only makes sense if you know which boundary your workload actually needs.

## Lab Focus
Use the lab to prove how virtualization evolved from hypervisors to OS-level isolation.
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
Then continue to [Linux Namespaces](../02-linux-namespaces/README.md).
