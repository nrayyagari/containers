# Networking Changes Lab

## Goal
Validate Kubernetes service discovery and observe policy-driven connectivity behavior.

## Prerequisites
- `kubectl` connected to a test cluster
- NetworkPolicy-capable CNI

## Steps
1. Create namespace and demo deployments:
   ```bash
   kubectl create ns net-mig
   kubectl -n net-mig create deployment web --image=nginx:1.27-alpine
   kubectl -n net-mig expose deployment web --port=80 --name web
   kubectl -n net-mig run client --image=alpine:3.20 --restart=Never --command -- sh -c 'sleep 3600'
   ```
2. Test DNS/service access:
   ```bash
   kubectl -n net-mig exec client -- sh -c 'apk add --no-cache curl >/dev/null && curl -I http://web'
   ```
3. Apply default deny ingress policy:
   ```bash
   cat <<'YAML' | kubectl -n net-mig apply -f -
   apiVersion: networking.k8s.io/v1
   kind: NetworkPolicy
   metadata:
     name: default-deny-ingress
   spec:
     podSelector: {}
     policyTypes: ["Ingress"]
   YAML
   ```
4. Re-test access (expect deny/timeout):
   ```bash
   kubectl -n net-mig exec client -- sh -c 'curl -m 5 -I http://web || true'
   ```
5. Add allow policy from client to web on port 80 and re-test.

## Verify
- Service DNS name `web` resolves from client pod.
- Connectivity changes after applying deny policy.
- Allow policy restores only intended traffic path.

## Cleanup
- `kubectl delete ns net-mig`
- Verify namespace is removed cleanly.

## Next
Adopt namespace-level baseline policies before migration waves.

## Concept Check
- Why is "pod IP reachable" not enough to declare networking healthy?
- What sequencing mistake in policy rollout causes accidental outages?
- Which metric/log proves policy impact versus app failure?

## Why This Lab Proves Understanding
- Verify checks discovery, segmentation, and controlled re-allow flow.
- Cleanup confirms environment reset and policy hygiene.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] Service DNS name `web` resolves from client pod.
- [ ] Connectivity changes after applying deny policy.
- [ ] Allow policy restores only intended traffic path.
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Policy effect cannot be demonstrated clearly.
- Environment not in clean state after cleanup.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
