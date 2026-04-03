# Host Networking Lab

## Goal
Develop hands-on confidence for Host Networking and prove understanding through observable output.

## Prerequisites
- Linux host only; host networking behaves differently on Docker Desktop.
- Port `8080` must be free on the host.
- Permission to run commands for this module.

## Steps
1. Run a web listener that shares the host network stack.
   COMMAND: docker run -d --name host-lab --network host python:3.12-alpine sh -c 'python -m http.server 8080'
2. Confirm the container is using host network mode.
   COMMAND: docker inspect host-lab --format '{{.HostConfig.NetworkMode}}'
3. Prove the listener is on the host socket table with no published port mapping.
   COMMAND: ss -ltnp | grep ':8080 '
4. Reach the service directly through the host loopback address.
   COMMAND: curl -I http://127.0.0.1:8080

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the host-networked container: docker rm -f host-lab 2>/dev/null || true

## Concept Check
- Which signal proves there is no separate container IP participating in this path?
- What operational risk appears immediately when two workloads expect the same port?
- Why is host networking usually the wrong default on a multi-tenant node?

## Why This Lab Proves Understanding
- It validates execution, interpretation, and operational cleanup.

## Answer Key
A lab is successful only when every Verify condition is true and cleanup is complete.

Pass criteria (all required):
- [ ] Steps completed and expected observations captured.
- [ ] Behavior explanation is accurate and mechanism-based.
- [ ] Failure mode and first diagnostic action documented.
- [ ] Cleanup completed with no leftover lab artifacts.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Output interpretation is unclear or incorrect.
- Environment is not clean after cleanup.
