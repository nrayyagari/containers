# Docker vs containerd

## Context & Problem
This topic explains how Docker and containerd differ in scope, UX, and Kubernetes fit. In production, this matters because runtime-layer confusion leads engineers to inspect or restart the wrong component.

## First Principles
- Runtime stacks are layered and each layer has a different responsibility.
- High-level managers handle images, snapshots, and lifecycle; low-level runtimes turn an OCI bundle into a running process.
- The authoritative troubleshooting tool depends on which layer created and now manages the workload.

## Production Implementation
Decide which layer is authoritative for the workload you are examining. For Kubernetes-managed containers, `crictl` and runtime-manager state usually matter more than Docker output, and low-level runtime evidence matters more than guesses.

## Troubleshooting Approach
Follow the request path one layer at a time: kubelet or CLI, runtime manager, shim, low-level runtime, and then the process itself. Restart nothing until you know which hop is lying or failing.

## Evolution & Alternatives
Docker bundled image building, CLI UX, and lifecycle management into one popular workflow. containerd narrowed the focus to runtime and image management, which is why Kubernetes moved toward CRI-native runtimes instead of Docker-specific node plumbing.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `systemctl status containerd --no-pager || true`
- `crictl info || true`
- `crictl ps -a || true`
- `docker ps -a || true`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- Which command output is authoritative for kubelet-managed runtime state?
- What node failure mode appears when CRI endpoint/runtime alignment is broken?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Low Level Runtime](../06-low-level-runtime/README.md).
