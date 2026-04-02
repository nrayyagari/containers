# Monitoring and Observability

## Context & Problem
This topic explains how Kubernetes changes what you observe and where you collect it. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.

## First Principles
- Kubernetes does not simply run your existing containers on a larger host pool; it changes the operating model around them.
- Pods, CRI-native runtimes, declarative rollout, cluster networking, and platform-managed configuration replace several Docker-era assumptions.
- A good migration document explains which assumption changed, why it changed, and how the new platform proves correctness.

## Production Implementation
Use this topic to challenge a Docker-era assumption directly. In migration work, the risk is not ignorance of YAML; it is keeping the old mental model after the platform boundary has changed.

## Troubleshooting Approach
When a migrated workload fails, identify which Docker-era assumption survived the move: runtime interface, networking model, configuration injection, Pod semantics, or storage attachment. That answer is usually the real fix path.

## Evolution & Alternatives
As workloads became ephemeral and scheduled, observability had to move from host-centric collection to label-, workload-, and trace-centric collection. Kubernetes does not remove the need for signals; it multiplies the places those signals must be correlated.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `kubectl create deployment obs-demo --image=nginx:1.27-alpine`
- `kubectl get pods -o wide`
- `kubectl get events --sort-by=.metadata.creationTimestamp | tail -n 20`
- `kubectl logs deploy/obs-demo --tail=20 || true`

### What Success Looks Like
- You can demonstrate one change-to-signal correlation.
- You defined one explicit rollback trigger threshold.
- You documented minimum required observability gates pre-cutover.

### Questions To Answer After The Lab
- Which signal correlation proved deployment change impact on system behavior?
- Why is pod Running an insufficient migration success indicator?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Containers](../../README.md).
