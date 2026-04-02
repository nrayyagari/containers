# RuntimeClass

## Context & Problem
This topic explains how Kubernetes selects different runtime handlers per workload. In production, this matters because runtime-layer confusion leads engineers to inspect or restart the wrong component.
RuntimeClass does not implement a runtime. It selects a handler that must already exist on the node.

## First Principles
- Runtime stacks are layered and each layer has a different responsibility.
- High-level managers handle images, snapshots, and lifecycle; low-level runtimes turn an OCI bundle into a running process.
- The authoritative troubleshooting tool depends on which layer created and now manages the workload.

## Production Implementation
Decide which layer is authoritative for the workload you are examining. For Kubernetes-managed containers, `crictl` and runtime-manager state usually matter more than Docker output, and low-level runtime evidence matters more than guesses.

## Troubleshooting Approach
Follow the request path one layer at a time: kubelet or CLI, runtime manager, shim, low-level runtime, and then the process itself. Restart nothing until you know which hop is lying or failing.

## Evolution & Alternatives
RuntimeClass appeared because one cluster can need different isolation or performance profiles for different workloads. It reflects a broader shift toward explicitly exposing runtime choice instead of hiding it under one default node configuration.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `ps -ef | grep -E "containerd|shim|runc" | grep -v grep | head -n 30`
- `docker run -d --name rt-lab alpine:3.20 sleep 300`
- `docker inspect rt-lab --format "{{.Id}} {{.State.Pid}}"`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- Which workload profile in your environment truly needs RuntimeClass separation?
- What security/performance risk appears if RuntimeClass is misapplied broadly?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Networking](../../05-networking/README.md).
