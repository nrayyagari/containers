# CRI Compatibility

## Context & Problem
This topic explains what runtime compatibility requirements kubelet expects from a node. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.

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
- `cat /etc/crictl.yaml 2>/dev/null || echo "crictl config missing"`
- `crictl info || true`
- `ps -ef | grep kubelet | grep -E 'container-runtime-endpoint|cri' || true`
- `journalctl -u kubelet --no-pager | grep -Ei 'runtime|cri|socket|containerd' | tail -n 30`

### What Success Looks Like
- Runtime endpoint path is explicitly identified.
- crictl and kubelet endpoint settings are consistent.
- No unresolved CRI socket errors remain after validation.

### Questions To Answer After The Lab
- Which endpoint mismatch would cause kubelet-runtime communication failure?
- Which log signal confirms CRI recovery after fixing endpoint config?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Image Format](../03-image-format/README.md).
