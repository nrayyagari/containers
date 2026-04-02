# Process Isolation

## What It Is
A container is still a normal Linux process running on the host kernel. The difference is that the process runs with isolated views and restricted resources.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- A containerized process is still scheduled by the same host kernel as other processes.
- Isolation comes from constrained visibility, resources, and privilege, not from a new kernel.
- Host-level tools remain valid because the process is still a host process underneath.

## Lab Focus
Use the lab to prove why a container is still a host process.
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
Then continue to [Kernel Features](../06-kernel-features/README.md).
