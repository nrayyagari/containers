# Config Secrets Lab

## Goal
Separate non-sensitive config from secrets and validate runtime injection.

## Prerequisites
- kubectl access to a test cluster.

## Steps
1. Create config and secret.
   COMMAND: kubectl create configmap app-config --from-literal=APP_MODE=staging
   COMMAND: kubectl create secret generic app-secret --from-literal=DB_PASSWORD=demo-pass
2. Create pod consuming both resources.
   COMMAND: kubectl run config-check --image=alpine:3.20 --restart=Never --env-from=configmap/app-config --env-from=secret/app-secret --command -- sh -c 'sleep 300'
3. Validate env injection.
   COMMAND: kubectl exec config-check -- printenv | grep APP_MODE
   COMMAND: kubectl exec config-check -- printenv | grep DB_PASSWORD

## Expected Observations
- Both config and secret values are injected from Kubernetes resources.
- Resource types remain separate and purpose-specific.
- You can explain rotation without rebuilding image.

## Verify
- Config value resolved in pod.
- Secret value resolved in pod.
- Rotation rationale documented.

## Cleanup
- COMMAND: kubectl delete pod config-check --ignore-not-found
- COMMAND: kubectl delete configmap app-config --ignore-not-found
- COMMAND: kubectl delete secret app-secret --ignore-not-found

## Concept Check
- Why is baking secrets into images unsafe even with private registry?
- Which event should trigger immediate secret rotation?
- How do you detect accidental secret leak in logs/manifests?

## Why This Lab Proves Understanding
- You validated separation of concerns with live workload evidence.

## Answer Key
Pass when all Verify points are satisfied and cleanup is complete.
