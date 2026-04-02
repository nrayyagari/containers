# Deployment Strategies Lab

## Goal
Evaluate rollout options and practice safe rollback logic for Kubernetes migration.

## Prerequisites
- `kubectl` connected to a test cluster (kind/minikube acceptable)

## Steps
1. Create baseline deployment:
   ```bash
   kubectl create deployment rollout-demo --image=nginx:1.27-alpine
   kubectl expose deployment rollout-demo --port=80 --type=ClusterIP
   ```
2. Configure rolling strategy and verify:
   ```bash
   kubectl patch deployment rollout-demo -p '{"spec":{"strategy":{"type":"RollingUpdate","rollingUpdate":{"maxUnavailable":1,"maxSurge":1}}}}'
   kubectl rollout status deployment/rollout-demo
   ```
3. Trigger update:
   ```bash
   kubectl set image deployment/rollout-demo nginx=nginx:1.27
   kubectl rollout status deployment/rollout-demo
   ```
4. View rollout history:
   ```bash
   kubectl rollout history deployment/rollout-demo
   ```
5. Roll back to previous revision:
   ```bash
   kubectl rollout undo deployment/rollout-demo
   kubectl rollout status deployment/rollout-demo
   ```

## Verify
- Rolling update completes successfully.
- Rollout history shows at least one previous revision.
- Rollback returns deployment to healthy state.

## Cleanup
- `kubectl delete svc rollout-demo`
- `kubectl delete deployment rollout-demo`

## Next
Add canary tooling only after baseline rolling + rollback is reliable.

## Concept Check
- Why is rollback speed often more important than perfect prevention?
- What readiness/probe mistake can make rolling updates unsafe?
- When should you prefer canary over plain rolling update?

## Why This Lab Proves Understanding
- Verify checks full release cycle: deploy, update, observe, recover.
- Cleanup confirms disciplined teardown in shared test clusters.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] Rolling update completes successfully.
- [ ] Rollout history shows at least one previous revision.
- [ ] Rollback returns deployment to healthy state.
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Rollback path not validated.
- Environment not in clean state after cleanup.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
