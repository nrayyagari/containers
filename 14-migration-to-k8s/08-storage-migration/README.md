# Storage Migration

## Context & Problem
This topic explains how persistent data semantics change when workloads become scheduled rather than host-pinned. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.

## First Principles
- Container storage has multiple lifecycles: image layers, writable layers, volumes, and external storage backends.
- Copy-on-write and overlay behavior can change both performance and the meaning of a write operation.
- Durability depends on where data lives, not on whether the application wrote it successfully once.

## Production Implementation
Use this topic to challenge a Docker-era assumption directly. In migration work, the risk is not ignorance of YAML; it is keeping the old mental model after the platform boundary has changed.

## Troubleshooting Approach
Ask three questions early: where does the data live, who owns it, and what path exposes it to the process? That separates permission problems from backend problems and durability problems from simple path mistakes.

## Evolution & Alternatives
Migration thinking changed after dockershim removal and the rise of CRI-native nodes. The successful path now is to adopt Kubernetes-native operating concepts rather than preserve Docker-era habits behind new YAML.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `kubectl apply -f - <<'YAML'`
- `kubectl apply -f - <<'YAML'`
- `kubectl exec pvc-writer -- cat /data/value.txt`
- `kubectl delete pod pvc-writer`

### What Success Looks Like
- PVC in Bound state.
- Data present before and after pod recreation.
- You documented one reclaim-policy risk.

### Questions To Answer After The Lab
- Which evidence proves persistence across pod recreation, not just restart luck?
- What reclaim-policy misunderstanding can cause irreversible data loss?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Service Mesh](../09-service-mesh/README.md).
