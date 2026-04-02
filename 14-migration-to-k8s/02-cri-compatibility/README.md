# CRI Compatibility

## What It Is
CRI Compatibility covers What runtime compatibility kubelet expects from a node.

## Why It Matters
It matters because Kubernetes migration fails when Docker assumptions are copied over unchanged.

## Key Points
- Runtime stacks are layered and each layer has a different job.
- High-level managers handle images and lifecycle; low-level runtimes create the process.
- Use tools that match the layer that owns the workload.

## Lab Focus
Use the lab to prove what runtime compatibility kubelet expects from a node.
- Key commands:
  - `cat /etc/crictl.yaml 2>/dev/null || echo "crictl config missing"`
  - `crictl info || true`
  - `ps -ef | grep kubelet | grep -E 'container-runtime-endpoint|cri' || true`
- Finish only when:
  - Runtime endpoint path is explicitly identified.
  - crictl and kubelet endpoint settings are consistent.

## Common Mistakes
- Collapsing several runtime layers into 'Docker is broken'.
- Using the wrong CLI for the layer that owns the workload.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Image Format](../03-image-format/README.md).
