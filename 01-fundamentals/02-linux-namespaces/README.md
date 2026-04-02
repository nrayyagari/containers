# Linux Namespaces

## What It Is
Linux namespaces give a process its own view of resources such as PIDs, mounts, networks, IPC, hostname, and user IDs. They isolate visibility, not the underlying host.

## Why It Matters
If the wrong namespace is shared, a workload can see or affect more of the host than intended.

## Key Points
- Each namespace type isolates one category of resources, not everything.
- PID and network namespaces are usually the easiest places to prove isolation.
- Namespaces alone are not a complete container boundary; cgroups and security controls still matter.

## Lab Focus
Use the lab to prove how processes get isolated views of PIDs, mounts, networks, IPC, UTS, and users.
- Key commands:
  - `docker run -d --name ns-lab alpine:3.20 sleep 300`
  - `ps -ef | head -n 10`
  - `docker exec ns-lab ps -ef`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Treating one namespace as the whole container boundary.
- Debugging app config before checking which namespace is actually shared.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Control Groups and cgroups](../03-control-groups-cgroups/README.md).
