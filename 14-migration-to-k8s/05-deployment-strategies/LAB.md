# Deployment Strategies Lab

## Goal
Practice rollout and rollback flow with explicit verification.

## Prerequisites
- kubectl access to a test cluster.

## Steps
1. Create deployment.
   COMMAND: kubectl create deployment rollout-demo --image=nginx:1.27-alpine
2. Update image and watch rollout.
   COMMAND: kubectl set image deployment/rollout-demo nginx=nginx:1.27
   COMMAND: kubectl rollout status deployment/rollout-demo
3. Inspect rollout history.
   COMMAND: kubectl rollout history deployment/rollout-demo
4. Execute rollback and verify.
   COMMAND: kubectl rollout undo deployment/rollout-demo
   COMMAND: kubectl rollout status deployment/rollout-demo

## Expected Observations
- Rollout completes with revision history.
- Rollback path is functional and observable.
- You can describe trigger conditions for rollback.

## Verify
- Successful rollout observed.
- Successful rollback observed.
- You documented one production rollback trigger.

## Cleanup
- COMMAND: kubectl delete deployment rollout-demo --ignore-not-found

## Concept Check
- Which rollout/rollback evidence shows release safety is actually working?
- What probe or readiness mistake can turn rollout into outage?
- Which explicit rollback trigger should be documented before migration wave?

## Why This Lab Proves Understanding
- You exercised full release safety cycle, not only deployment creation.

## Answer Key
Pass when all Verify points are satisfied and cleanup is complete.
