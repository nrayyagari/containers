# Linux Namespaces

## Context & Problem
This topic explains how the kernel gives processes isolated views of PIDs, mounts, networks, IPC, UTS, and users. In production, this matters because every higher-level tool depends on these boundaries behaving exactly as the kernel defines them.
A namespace is not a whole container by itself; it is one scoped view of one class of system resources.

## First Principles
- Namespaces change what a process can see, not what the host physically contains.
- Different namespace types isolate different resources: PID, network, mount, IPC, UTS, and user IDs.
- A convincing container boundary appears only when namespaces are combined with cgroups, a filesystem, and security policy.

## Production Implementation
Treat this as a kernel boundary first and a container feature second. Validate it from host evidence such as namespace links, cgroup files, mount state, capability sets, or security policy before you trust higher-level tooling.

## Troubleshooting Approach
When isolation looks wrong, compare namespace links under `/proc/<pid>/ns` and decide which namespace is actually shared. Do not start with firewall or filesystem changes until you know the scope is correct.

## Evolution & Alternatives
These primitives predate modern container branding. The tooling changed, but the Linux kernel mechanisms remained the foundation, which is why low-level understanding still matters in modern platforms.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `docker run -d --name ns-lab alpine:3.20 sleep 300`
- `ps -ef | head -n 10`
- `docker exec ns-lab ps -ef`
- `pid=$(docker inspect -f '{{.State.Pid}}' ns-lab); ls -l /proc/$pid/ns`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- Which namespace output line best proves process/visibility isolation?
- What breaks if PID or network namespace assumptions are wrong?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Control Groups and cgroups](../03-control-groups-cgroups/README.md).
