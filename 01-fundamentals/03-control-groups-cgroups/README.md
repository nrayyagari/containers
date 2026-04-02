# Control Groups and cgroups

## What It Is
cgroups organize processes into groups and let the kernel apply CPU, memory, and I/O controls to those groups. They are the resource-control half of container isolation.

## Why It Matters
If resource control is misunderstood, teams blame the app when the kernel is actually throttling or killing it.

## Key Points
- cgroups control resources at the kernel level, not at the application level.
- Throttling, reclaim pressure, and OOM kills are observable signs of enforcement.
- cgroup v2 unifies the hierarchy and makes controller behavior more consistent.

## Lab Focus
Use the lab to prove how Linux enforces CPU, memory, and I/O limits.
- Key commands:
  - `docker run -d --name cg-lab --memory=128m alpine:3.20 sleep 300`
  - `docker inspect cg-lab --format "{{.HostConfig.Memory}}"`
  - `pid=$(docker inspect -f '{{.State.Pid}}' cg-lab); cat /proc/$pid/cgroup`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Looking only at app logs and missing kernel enforcement signals.
- Changing limits before confirming whether pressure or throttling is the real issue.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Union Filesystems](../04-union-filesystems/README.md).
