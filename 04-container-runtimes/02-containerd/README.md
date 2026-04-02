# Containerd

## What It Is
containerd is a high-level container runtime manager. It handles images, snapshots, tasks, and runtime integration, while lower-level runtimes such as `runc` create the actual process.

## Why It Matters
It is the source of truth for many Kubernetes nodes, so Docker output can mislead you.

## Key Points
- Runtime stacks are layered and each layer has a different job.
- High-level managers handle images and lifecycle; low-level runtimes create the process.
- Use tools that match the layer that owns the workload.

## Lab Focus
Use the lab to prove how containerd manages images, snapshots, tasks, and runtime integration.
- Key commands:
  - `systemctl status containerd --no-pager || true`
  - `crictl info || true`
  - `crictl ps -a || true`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Using Docker output as the source of truth for kubelet-managed workloads.
- Restarting the runtime before identifying which layer is actually failing.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [CRI](../03-cri/README.md).
