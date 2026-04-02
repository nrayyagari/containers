# Deployment Strategies

## What It Is
Deployment Strategies covers How rollout strategy changes migration risk.

## Why It Matters
It matters because Kubernetes migration fails when Docker assumptions are copied over unchanged.

## Key Points
- Kubernetes changes the operating model, not just the syntax.
- Pods, CRI, declarative rollout, and cluster networking replace Docker-era assumptions.
- Migration work succeeds when those assumption changes are explicit.

## Lab Focus
Use the lab to prove how rollout strategy changes migration risk.
- Key commands:
  - `kubectl create deployment rollout-demo --image=nginx:1.27-alpine`
  - `kubectl set image deployment/rollout-demo nginx=nginx:1.27`
  - `kubectl rollout status deployment/rollout-demo`
- Finish only when:
  - Successful rollout observed.
  - Successful rollback observed.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Config and Secrets](../06-config-secrets/README.md).
