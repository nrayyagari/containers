# Monitoring and Observability Lab

## Goal
Create a migration-ready observability checklist and validate core Kubernetes troubleshooting signals.

## Prerequisites
- `kubectl` connected to test cluster
- Access to logs/metrics stack (or `kubectl` events/logs as minimum)

## Steps
1. Deploy sample workload:
   ```bash
   kubectl create deployment obs-demo --image=nginx:1.27-alpine
   kubectl expose deployment obs-demo --port=80 --type=ClusterIP
   ```
2. Capture baseline signals:
   ```bash
   kubectl get pods -o wide
   kubectl top pods || true
   kubectl get events --sort-by=.metadata.creationTimestamp | tail -n 20
   ```
3. Trigger a controlled change:
   ```bash
   kubectl set image deployment/obs-demo nginx=nginx:1.27
   kubectl rollout status deployment/obs-demo
   ```
4. Correlate rollout with logs/events:
   ```bash
   kubectl describe deployment obs-demo | sed -n '1,120p'
   kubectl logs deploy/obs-demo --tail=50
   ```
5. Write a migration checklist with minimum required signals:
   - Error rate, latency, saturation, availability
   - Pod restarts, probe failures, rollout status
   - Cluster events and namespace-level anomalies

## Verify
- You captured baseline and post-change signals.
- You can correlate one deployment change to at least one observable signal.
- You created a reusable migration observability checklist.

## Cleanup
- `kubectl delete svc obs-demo --ignore-not-found`
- `kubectl delete deployment obs-demo --ignore-not-found`

## Next
Convert checklist into pre-flight and post-deploy gates in CI/CD.

## Concept Check
- Why is "pod is Running" insufficient as a migration success signal?
- Which two signals best detect silent correctness regressions?
- What is your rollback trigger threshold, and why?

## Why This Lab Proves Understanding
- Verify checks signal collection, correlation, and operational decision criteria.
- Cleanup confirms repeatable lab hygiene.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] You captured baseline and post-change signals.
- [ ] You can correlate one deployment change to at least one observable signal.
- [ ] You created a reusable migration observability checklist.
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- No clear correlation between change and signal.
- Environment not in clean state after cleanup.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
