# Union Filesystems

## Context & Problem
This topic explains how layered filesystems build a writable container root from read-only image layers. In production, this matters because every higher-level tool depends on these boundaries behaving exactly as the kernel defines them.
A union filesystem is not durable application storage. It is a layering mechanism that makes image reuse practical.

## First Principles
- Container storage has multiple lifecycles: image layers, writable layers, volumes, and external storage backends.
- Copy-on-write and overlay behavior can change both performance and the meaning of a write operation.
- Durability depends on where data lives, not on whether the application wrote it successfully once.

## Production Implementation
Treat this as a kernel boundary first and a container feature second. Validate it from host evidence such as namespace links, cgroup files, mount state, capability sets, or security policy before you trust higher-level tooling.

## Troubleshooting Approach
Ask three questions early: where does the data live, who owns it, and what path exposes it to the process? That separates permission problems from backend problems and durability problems from simple path mistakes.

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
- Which observation proves writable container layer behavior vs image layers?
- Why can ignoring copy-on-write behavior cause storage surprises?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Process Isolation](../05-process-isolation/README.md).
