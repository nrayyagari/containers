# Cgroups Deep Dive

## Context & Problem
This topic explains how controllers, hierarchies, and pressure signals behave under load. In production, this matters because every higher-level tool depends on these boundaries behaving exactly as the kernel defines them.
A cgroup does not make a workload efficient. It only organizes and constrains what the kernel will allow that workload to consume.

## First Principles
- cgroups organize processes into a hierarchy and apply controller-specific rules to those groups.
- Resource problems show up as measurable kernel behavior such as throttling, reclaim pressure, or OOM kills.
- If you only look at the application, you will miss the host-level control that actually constrained it.

## Production Implementation
Treat this as a kernel boundary first and a container feature second. Validate it from host evidence such as namespace links, cgroup files, mount state, capability sets, or security policy before you trust higher-level tooling.

## Troubleshooting Approach
Separate application inefficiency from kernel enforcement. Check for throttling, reclaim pressure, and OOM evidence before changing limits or blaming the scheduler.

## Evolution & Alternatives
These primitives predate modern container branding. The tooling changed, but the Linux kernel mechanisms remained the foundation, which is why low-level understanding still matters in modern platforms.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `docker run -d --name cg-lab --memory=128m alpine:3.20 sleep 300`
- `docker inspect cg-lab --format "{{.HostConfig.Memory}}"`
- `pid=$(docker inspect -f '{{.State.Pid}}' cg-lab); cat /proc/$pid/cgroup`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- Which metric or file proves cgroup enforcement is active?
- What failure mode appears when limits are set but not enforced as expected?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Isolation Summary](../12-isolation-summary/README.md).
