# Cgroups Deep Dive

## What It Is
Cgroups Deep Dive covers How controllers and pressure signals behave under load.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- cgroups control resources at the kernel level, not at the application level.
- Throttling, reclaim pressure, and OOM kills are observable signs of enforcement.
- cgroup v2 unifies the hierarchy and makes controller behavior more consistent.

## Lab Focus
Use the lab to prove how controllers and pressure signals behave under load.
- Key commands:
  - `docker run -d --name cg-lab --memory=128m alpine:3.20 sleep 300`
  - `docker inspect cg-lab --format "{{.HostConfig.Memory}}"`
  - `pid=$(docker inspect -f '{{.State.Pid}}' cg-lab); cat /proc/$pid/cgroup`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Isolation Summary](../12-isolation-summary/README.md).
