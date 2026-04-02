# Pod Concept

## What It Is
A Pod is the smallest deployable unit in Kubernetes. Containers in the same Pod share a network namespace and lifecycle context, which is why a Pod is not just 'a group of containers'.

## Why It Matters
Many migration bugs come from assuming a Pod is just 'multiple containers together'.

## Key Points
- Kubernetes changes the operating model, not just the syntax.
- Pods, CRI, declarative rollout, and cluster networking replace Docker-era assumptions.
- Migration work succeeds when those assumption changes are explicit.

## Lab Focus
Use the lab to prove why a Pod is a scheduling and lifecycle unit, not just grouped containers.
- Key commands:
  - `docker network create pod-sim-net`
  - `docker run -d --name pod-app --network pod-sim-net nginx:1.27-alpine`
  - `docker run --rm --network pod-sim-net alpine:3.20 sh -c 'apk add --no-cache curl >/dev/null && curl -I http://pod-app'`
- Finish only when:
  - Connectivity test succeeds.
  - You documented two accurate pod-vs-network differences.

## Common Mistakes
- Treating a Pod as an arbitrary grouping mechanism.
- Colocating unrelated containers that should scale or fail independently.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Deployment Strategies](../05-deployment-strategies/README.md).
