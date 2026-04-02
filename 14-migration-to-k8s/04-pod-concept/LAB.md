# Pod Concept Lab

## Goal
Understand pod-style co-location using shared networking and process behavior.

## Prerequisites
- Docker installed

## Steps
1. Create a shared network:
   ```bash
   docker network create pod-sim-net
   ```
2. Start a web container:
   ```bash
   docker run -d --name pod-app --network pod-sim-net nginx:1.27-alpine
   ```
3. Start a "sidecar-like" diagnostics container in same network:
   ```bash
   docker run --rm --name pod-sidecar --network pod-sim-net alpine:3.20 sh -c 'apk add --no-cache curl >/dev/null && curl -I http://pod-app'
   ```
4. Inspect communication assumption:
   ```bash
   docker exec pod-app hostname
   docker network inspect pod-sim-net | head -n 40
   ```
5. Record differences between this simulation and real Kubernetes pod behavior.

## Verify
- Sidecar-like container reaches app container by service name.
- You can explain at least two differences between shared Docker network and real pod namespaces.
- You identified one case where sidecar pattern is appropriate.

## Cleanup
- `docker rm -f pod-app || true`
- `docker network rm pod-sim-net || true`

## Next
Practice with real pods in `repos/kubernetes` to observe native behavior.

## Concept Check
- Why is "one pod = one container" an incomplete mental model?
- Which workload pair belongs together in one pod, and which should be split?
- Which pod-level signal matters most when debugging crash loops?

## Why This Lab Proves Understanding
- Verify checks both command execution and architectural reasoning.
- Cleanup confirms you can safely reset test artifacts.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] Sidecar-like container reaches app container by service name.
- [ ] You can explain at least two differences between shared Docker network and real pod namespaces.
- [ ] You identified one case where sidecar pattern is appropriate.
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Conceptual comparison is inaccurate.
- Environment not in clean state after cleanup.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
