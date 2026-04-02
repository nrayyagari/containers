# Isolation Summary

## Context & Problem
This topic explains how namespaces, cgroups, layered filesystems, and security policy combine into a container. In production, this matters because every higher-level tool depends on these boundaries behaving exactly as the kernel defines them.

## First Principles
- No single feature creates a safe container boundary on its own.
- Real isolation is the composition of what the process can see, what it can consume, what filesystem it can change, and which privileged actions it can still perform.
- Summarizing the model matters because most production incidents involve at least two of those layers at once.

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
- Which control boundary is easiest to verify quickly during incident response?
- Which boundary is most often misunderstood by new platform engineers?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Docker Basics](../../02-docker-basics/README.md).
