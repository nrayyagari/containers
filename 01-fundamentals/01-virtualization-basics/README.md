# Virtualization Basics

## Context & Problem
This topic explains how virtualization evolved from hardware emulation and hypervisors to OS-level isolation. In production, this matters because every higher-level tool depends on these boundaries behaving exactly as the kernel defines them.

## First Principles
- Virtualization is an isolation strategy, not one single implementation.
- Hypervisors isolate at a hardware or virtual-hardware boundary, while containers isolate within one shared host kernel.
- Understanding that boundary explains why containers are lighter and faster to start, but also why they cannot claim VM-style isolation by default.

## Production Implementation
Treat this as a kernel boundary first and a container feature second. Validate it from host evidence such as namespace links, cgroup files, mount state, capability sets, or security policy before you trust higher-level tooling.

## Troubleshooting Approach
Start with direct evidence at the layer this topic controls, then expand outward only if the observed state matches expectations.

## Evolution & Alternatives
These primitives predate modern container branding. The tooling changed, but the Linux kernel mechanisms remained the foundation, which is why low-level understanding still matters in modern platforms.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `docker run -d --name fnd-lab alpine:3.20 sleep 300`
- `docker inspect fnd-lab --format "{{.State.Pid}} {{.State.Status}}"`
- `docker exec fnd-lab cat /proc/1/status | sed -n '1,25p'`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- What kernel-sharing evidence proves this is a container, not a VM?
- Which workload should still prefer a VM boundary, and why?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Linux Namespaces](../02-linux-namespaces/README.md).
