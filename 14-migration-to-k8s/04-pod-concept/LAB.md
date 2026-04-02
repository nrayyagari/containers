# Pod Concept Lab

## Goal
Understand pod-style co-location and why it is not equivalent to arbitrary container grouping.

## Prerequisites
- Docker installed.

## Steps
1. Create shared test network.
   COMMAND: docker network create pod-sim-net
2. Start app container.
   COMMAND: docker run -d --name pod-app --network pod-sim-net nginx:1.27-alpine
3. Run sidecar-like check container.
   COMMAND: docker run --rm --network pod-sim-net alpine:3.20 sh -c 'apk add --no-cache curl >/dev/null && curl -I http://pod-app'
4. Capture differences from real Kubernetes pod behavior.

## Expected Observations
- Sidecar-like container reaches app over shared network.
- Shared network alone does not equal full pod lifecycle semantics.
- You can list at least two differences from real pods.

## Verify
- Connectivity test succeeds.
- You documented two accurate pod-vs-network differences.
- You identified one valid sidecar use case.

## Cleanup
- COMMAND: docker rm -f pod-app 2>/dev/null || true
- COMMAND: docker network rm pod-sim-net 2>/dev/null || true

## Concept Check
- Why is one-pod-equals-one-container an incomplete model?
- What should never be colocated in one pod?
- Which pod-level signal is critical during crash-loop triage?

## Why This Lab Proves Understanding
- You validated both behavioral and architectural differences.

## Answer Key
Pass when all Verify points are satisfied and cleanup is complete.
