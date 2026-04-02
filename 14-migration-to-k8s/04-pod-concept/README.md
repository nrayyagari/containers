# Pod Concept

## Context & Problem
This topic explains why a Kubernetes Pod is a scheduling and lifecycle unit, not just grouped containers. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.
A Pod is not an arbitrary bag of containers. It is a deliberately shared execution context and scheduling unit.

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
- `docker network create pod-sim-net`
- `docker run -d --name pod-app --network pod-sim-net nginx:1.27-alpine`
- `docker run --rm --network pod-sim-net alpine:3.20 sh -c 'apk add --no-cache curl >/dev/null && curl -I http://pod-app'`
- `docker rm -f pod-app 2>/dev/null || true`

### What Success Looks Like
- Connectivity test succeeds.
- You documented two accurate pod-vs-network differences.
- You identified one valid sidecar use case.

### Questions To Answer After The Lab
- Which observation in this lab disproves one-container-equals-one-pod thinking?
- What architecture mistake appears when unrelated containers are colocated?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Deployment Strategies](../05-deployment-strategies/README.md).
