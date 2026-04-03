# Bridge Networking Lab

## Goal
Develop hands-on confidence for Bridge Networking and prove understanding through observable output.

## Prerequisites
- Non-production Linux host with Docker Engine.
- Basic network tools available: `ip`, `ping`, and `docker network inspect`.
- Permission to run commands for this module.

## Steps
1. Create a user-defined bridge network.
   COMMAND: docker network create br-lab
2. Start two containers on that bridge.
   COMMAND: docker run -d --name br-a --network br-lab alpine:3.20 sleep 300
   COMMAND: docker run -d --name br-b --network br-lab alpine:3.20 sleep 300
3. Prove service-name reachability from one container to the other.
   COMMAND: docker exec br-a ping -c1 br-b
4. Inspect the bridge network and record subnet, gateway, and attached endpoints.
   COMMAND: docker network inspect br-lab

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove lab containers and network: docker rm -f br-a br-b 2>/dev/null || true; docker network rm br-lab 2>/dev/null || true

## Concept Check
- Which output proves Docker provided name resolution for `br-b` instead of static host entries?
- What breaks first if this bridge subnet overlaps with another routed subnet on the host or VPN?
- Which host-side signal would you inspect before changing any application configuration?

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
