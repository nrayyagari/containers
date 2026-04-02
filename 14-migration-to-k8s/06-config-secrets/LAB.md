# Config and Secrets Lab

## Goal
Inject non-sensitive config and sensitive values separately into a workload.

## Prerequisites
- `kubectl` connected to a test cluster

## Steps
1. Create config and secret:
   ```bash
   kubectl create configmap app-config --from-literal=APP_MODE=staging
   kubectl create secret generic app-secret --from-literal=DB_PASSWORD='p@ssw0rd-demo'
   ```
2. Create pod using both resources:
   ```bash
   cat <<'YAML' | kubectl apply -f -
   apiVersion: v1
   kind: Pod
   metadata:
     name: config-secret-demo
   spec:
     containers:
     - name: app
       image: alpine:3.20
       command: ["sh","-c","sleep 3600"]
       envFrom:
       - configMapRef:
           name: app-config
       - secretRef:
           name: app-secret
   YAML
   ```
3. Verify injected values:
   ```bash
   kubectl exec config-secret-demo -- printenv | grep APP_MODE
   kubectl exec config-secret-demo -- printenv | grep DB_PASSWORD
   ```
4. Confirm secret object exists but should never be printed in plaintext logs.
5. Record a secret-rotation trigger event for your team.

## Verify
- Pod reads config and secret values from Kubernetes objects.
- Config and secret are stored as separate resources.
- You can explain why secret rotation should not require image rebuild.

## Cleanup
- `kubectl delete pod config-secret-demo --ignore-not-found`
- `kubectl delete configmap app-config --ignore-not-found && kubectl delete secret app-secret --ignore-not-found`

## Next
Integrate external secret manager and rotation automation.

## Concept Check
- Why is baking secrets into image layers dangerous even in private registries?
- What operational event should trigger secret rotation immediately?
- How would you detect accidental secret exposure in logs or manifests?

## Why This Lab Proves Understanding
- Verify confirms correct separation of concerns and runtime injection model.
- Cleanup confirms secure teardown of credential artifacts.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] Pod reads config and secret values from Kubernetes objects.
- [ ] Config and secret are stored as separate resources.
- [ ] You can explain why secret rotation should not require image rebuild.
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Separation between config and secret is unclear.
- Environment not in clean state after cleanup.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
