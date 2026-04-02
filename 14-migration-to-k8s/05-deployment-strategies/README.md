# Deployment Strategies

## Context & Problem
This topic explains how rolling, blue or green, and canary rollouts change migration risk. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.

## First Principles
- Kubernetes does not simply run your existing containers on a larger host pool; it changes the operating model around them.
- Pods, CRI-native runtimes, declarative rollout, cluster networking, and platform-managed configuration replace several Docker-era assumptions.
- A good migration document explains which assumption changed, why it changed, and how the new platform proves correctness.

## Production Implementation
Use this topic to challenge a Docker-era assumption directly. In migration work, the risk is not ignorance of YAML; it is keeping the old mental model after the platform boundary has changed.

## Troubleshooting Approach
When a migrated workload fails, identify which Docker-era assumption survived the move: runtime interface, networking model, configuration injection, Pod semantics, or storage attachment. That answer is usually the real fix path.

## Evolution & Alternatives
Migration thinking changed after dockershim removal and the rise of CRI-native nodes. The successful path now is to adopt Kubernetes-native operating concepts rather than preserve Docker-era habits behind new YAML.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `kubectl create deployment rollout-demo --image=nginx:1.27-alpine`
- `kubectl set image deployment/rollout-demo nginx=nginx:1.27`
- `kubectl rollout status deployment/rollout-demo`
- `kubectl rollout history deployment/rollout-demo`

### What Success Looks Like
- Successful rollout observed.
- Successful rollback observed.
- You documented one production rollback trigger.

### Questions To Answer After The Lab
- Which rollout/rollback evidence shows release safety is actually working?
- What probe or readiness mistake can turn rollout into outage?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Config and Secrets](../06-config-secrets/README.md).
