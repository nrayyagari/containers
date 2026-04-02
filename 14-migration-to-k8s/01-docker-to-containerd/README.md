# Docker To Containerd

## Context & Problem
This topic explains why Kubernetes nodes moved from Docker-centric plumbing to CRI-native runtimes. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.

## First Principles
- Runtime stacks are layered and each layer has a different responsibility.
- High-level managers handle images, snapshots, and lifecycle; low-level runtimes turn an OCI bundle into a running process.
- The authoritative troubleshooting tool depends on which layer created and now manages the workload.

## Production Implementation
Use this topic to challenge a Docker-era assumption directly. In migration work, the risk is not ignorance of YAML; it is keeping the old mental model after the platform boundary has changed.

## Troubleshooting Approach
Follow the request path one layer at a time: kubelet or CLI, runtime manager, shim, low-level runtime, and then the process itself. Restart nothing until you know which hop is lying or failing.

## Evolution & Alternatives
Migration thinking changed after dockershim removal and the rise of CRI-native nodes. The successful path now is to adopt Kubernetes-native operating concepts rather than preserve Docker-era habits behind new YAML.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `systemctl status docker --no-pager || true`
- `systemctl status containerd --no-pager || true`
- `docker pull alpine:3.20`
- `docker images | grep alpine`

### What Success Looks Like
- You identified the node runtime command set to use in Kubernetes incidents.
- You captured evidence for Docker-vs-CRI view differences.
- You documented one diagnostic rule for your runbook.

### Questions To Answer After The Lab
- Which command pair proves Docker and CRI views can diverge on Kubernetes nodes?
- What migration risk appears when teams keep Docker-only troubleshooting habits?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [CRI Compatibility](../02-cri-compatibility/README.md).
