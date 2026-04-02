# Docker To Containerd

## What It Is
Docker To Containerd covers Why Kubernetes nodes moved from Docker-centric plumbing to CRI-native runtimes.

## Why It Matters
It matters because Kubernetes migration fails when Docker assumptions are copied over unchanged.

## Key Points
- Runtime stacks are layered and each layer has a different job.
- High-level managers handle images and lifecycle; low-level runtimes create the process.
- Use tools that match the layer that owns the workload.

## Lab Focus
Use the lab to prove why Kubernetes nodes moved from Docker-centric plumbing to CRI-native runtimes.
- Key commands:
  - `systemctl status docker --no-pager || true`
  - `systemctl status containerd --no-pager || true`
  - `docker pull alpine:3.20`
- Finish only when:
  - You identified the node runtime command set to use in Kubernetes incidents.
  - You captured evidence for Docker-vs-CRI view differences.

## Common Mistakes
- Collapsing several runtime layers into 'Docker is broken'.
- Using the wrong CLI for the layer that owns the workload.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [CRI Compatibility](../02-cri-compatibility/README.md).
