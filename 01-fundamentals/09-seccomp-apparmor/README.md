# Seccomp Apparmor

## Context & Problem
This topic explains how syscall filtering and mandatory access control reduce kernel attack surface. In production, this matters because every higher-level tool depends on these boundaries behaving exactly as the kernel defines them.

## First Principles
- Security controls are layered; no single flag makes a workload safe.
- Least privilege means reducing both what the process is allowed to do and how much trust you place in the artifact it runs from.
- A control is only useful if you can explain what it blocks and how you will verify that block during troubleshooting.

## Production Implementation
Treat this as a kernel boundary first and a container feature second. Validate it from host evidence such as namespace links, cgroup files, mount state, capability sets, or security policy before you trust higher-level tooling.

## Troubleshooting Approach
If the workload fails after hardening, identify the blocking layer before loosening everything. Security debugging is safe only when you can say whether identity, policy, syscall filtering, or trust verification caused the failure.

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
- Which evidence confirms syscall/LSM controls are active on this host?
- What attack path opens when seccomp/AppArmor profiles are bypassed?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Namespaces Deep Dive](../10-namespaces-deep-dive/README.md).
