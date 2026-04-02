# Monitoring Observability Lab

## Goal
Build a migration observability checklist with baseline and post-change evidence.

## Prerequisites
- kubectl access to test cluster.
- Access to cluster events/logs and optional metrics stack.

## Steps
1. Deploy sample workload.
   COMMAND: kubectl create deployment obs-demo --image=nginx:1.27-alpine
2. Capture baseline signals.
   COMMAND: kubectl get pods -o wide
   COMMAND: kubectl get events --sort-by=.metadata.creationTimestamp | tail -n 20
   COMMAND: kubectl logs deploy/obs-demo --tail=20 || true
3. Trigger controlled change.
   COMMAND: kubectl set image deployment/obs-demo nginx=nginx:1.27
   COMMAND: kubectl rollout status deployment/obs-demo
4. Capture post-change signals and correlate.
   COMMAND: kubectl describe deployment obs-demo | sed -n '1,120p'
   COMMAND: kubectl logs deploy/obs-demo --tail=50
5. Produce checklist covering:
   - error rate, latency, saturation, availability
   - pod restarts, rollout status, probe failures
   - cluster events and namespace anomalies

## Expected Observations
- Baseline and post-change signals are captured.
- Deployment change correlates with observable system signals.
- Checklist is reusable for migration waves.

## Verify
- You can demonstrate one change-to-signal correlation.
- You defined one explicit rollback trigger threshold.
- You documented minimum required observability gates pre-cutover.

## Cleanup
- COMMAND: kubectl delete deployment obs-demo --ignore-not-found

## Concept Check
- Why is pod Running status insufficient as migration success signal?
- Which two signals detect silent correctness regressions earliest?
- What rollback trigger would you enforce and why?

## Why This Lab Proves Understanding
- You connected operational decisions to measurable telemetry.

## Answer Key
Pass when all Verify points are satisfied and cleanup is complete.
