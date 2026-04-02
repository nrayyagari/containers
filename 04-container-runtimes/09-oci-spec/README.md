# OCI Specifications

## Context & Problem
This topic explains how OCI specifications standardize image, runtime, and distribution behavior. In production, this matters because runtime-layer confusion leads engineers to inspect or restart the wrong component.

## First Principles
- Runtime stacks are layered and each layer has a different responsibility.
- High-level managers handle images, snapshots, and lifecycle; low-level runtimes turn an OCI bundle into a running process.
- The authoritative troubleshooting tool depends on which layer created and now manages the workload.

## Production Implementation
Decide which layer is authoritative for the workload you are examining. For Kubernetes-managed containers, `crictl` and runtime-manager state usually matter more than Docker output, and low-level runtime evidence matters more than guesses.

## Troubleshooting Approach
Follow the request path one layer at a time: kubelet or CLI, runtime manager, shim, low-level runtime, and then the process itself. Restart nothing until you know which hop is lying or failing.

## Evolution & Alternatives
The runtime ecosystem moved toward clearer interfaces and smaller responsibilities. That made the stack more composable, but it also means operators must know which layer they are standing on.

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
- Which process or metadata evidence proves low-level runtime execution path?
- What breaks when OCI/runtime assumptions differ across environments?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [RuntimeClass](../10-runtime-classes/README.md).
