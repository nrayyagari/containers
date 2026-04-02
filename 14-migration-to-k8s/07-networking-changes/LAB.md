# Networking Changes Lab

## Goal
Validate service discovery and policy-based connectivity control.

## Prerequisites
- kubectl access to a cluster with NetworkPolicy-capable CNI.

## Steps
1. Create namespace and workloads.
   COMMAND: kubectl create ns net-mig
   COMMAND: kubectl -n net-mig create deployment web --image=nginx:1.27-alpine
   COMMAND: kubectl -n net-mig expose deployment web --port=80 --name web
   COMMAND: kubectl -n net-mig run client --image=alpine:3.20 --restart=Never --command -- sh -c 'sleep 300'
2. Validate DNS/service access.
   COMMAND: kubectl -n net-mig exec client -- sh -c 'apk add --no-cache curl >/dev/null && curl -I http://web'
3. Apply default deny ingress policy.
   COMMAND: kubectl -n net-mig apply -f - <<'YAML'
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: deny-all-ingress
spec:
  podSelector: {}
  policyTypes:
  - Ingress
YAML
4. Re-test connectivity and observe deny behavior.
   COMMAND: kubectl -n net-mig exec client -- sh -c 'curl -m 5 -I http://web || true'

## Expected Observations
- Service discovery works before policy deny.
- Connectivity is blocked after deny policy.
- Policy behavior is observable and repeatable.

## Verify
- DNS/service access success before deny.
- Access blocked after deny.
- You documented required allow policy shape for restoration.

## Cleanup
- COMMAND: kubectl delete ns net-mig --ignore-not-found

## Concept Check
- Why is pod-IP reachability insufficient as health signal?
- Which rollout order causes policy outages?
- What signal differentiates policy deny from app failure?

## Why This Lab Proves Understanding
- You verified both service-discovery and segmentation behavior.

## Answer Key
Pass when all Verify points are satisfied and cleanup is complete.
