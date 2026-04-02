# Monitoring and Observability

## What It Is
Monitoring and Observability covers How Kubernetes changes what you observe and where you collect it.

## Why It Matters
It matters because Kubernetes migration fails when Docker assumptions are copied over unchanged.

## Key Points
- Kubernetes changes the operating model, not just the syntax.
- Pods, CRI, declarative rollout, and cluster networking replace Docker-era assumptions.
- Migration work succeeds when those assumption changes are explicit.

## Lab Focus
Use the lab to prove how Kubernetes changes what you observe and where you collect it.
- Key commands:
  - `kubectl create deployment obs-demo --image=nginx:1.27-alpine`
  - `kubectl get pods -o wide`
  - `kubectl get events --sort-by=.metadata.creationTimestamp | tail -n 20`
- Finish only when:
  - You can demonstrate one change-to-signal correlation.
  - You defined one explicit rollback trigger threshold.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Containers](../../README.md).
