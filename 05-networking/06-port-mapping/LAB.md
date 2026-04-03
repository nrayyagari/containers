# Port Mapping Lab

## Goal
Develop hands-on confidence for Port Mapping and prove understanding through observable output.

## Prerequisites
- Docker Engine and host port `8088` available.
- `curl` and `ss` available on the host.
- Permission to run commands for this module.

## Steps
1. Run a web container with a published host port.
   COMMAND: docker run -d --name port-lab -p 8088:80 nginx:1.27-alpine
2. Inspect Docker's view of the published mapping.
   COMMAND: docker port port-lab
   COMMAND: docker inspect port-lab --format '{{json .NetworkSettings.Ports}}'
3. Reach the service through the host address.
   COMMAND: curl -I http://127.0.0.1:8088
4. Inspect the host socket table and explain how traffic is redirected to the container.
   COMMAND: ss -ltnp | grep ':8088 ' || true

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the published-port container: docker rm -f port-lab 2>/dev/null || true

## Concept Check
- Which output proves the host port and container port are different objects with a translation between them?
- What is the first thing you would check if the container is healthy but the published port fails externally?
- Why does binding `0.0.0.0` versus `127.0.0.1` change the exposure risk immediately?

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
