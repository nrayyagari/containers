# Linux Capabilities

## Context & Problem
This topic explains how root privileges are split into smaller permission sets. In production, this matters because every higher-level tool depends on these boundaries behaving exactly as the kernel defines them.

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
- `docker run --rm --cap-drop ALL alpine:3.20 sh -c "id && ping -c1 127.0.0.1 || true"`
- `docker run --rm --cap-drop ALL --cap-add NET_RAW alpine:3.20 ping -c1 127.0.0.1`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- Which command result proved capability-based least privilege in practice?
- Why is add-only-required capability safer than default capability set?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Seccomp Apparmor](../09-seccomp-apparmor/README.md).
