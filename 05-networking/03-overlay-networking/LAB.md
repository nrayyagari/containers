# Overlay Networking Lab

## Goal
Develop hands-on confidence for Overlay Networking and prove understanding through observable output.

## Prerequisites
- Linux host with Docker Engine and permission to initialize single-node Swarm mode.
- No production Swarm should be using this host during the exercise.
- Permission to run commands for this module.

## Steps
1. Initialize Swarm mode if it is not already enabled.
   COMMAND: docker swarm init || true
2. Create an attachable overlay network.
   COMMAND: docker network create -d overlay --attachable ov-lab
3. Run two containers on the overlay.
   COMMAND: docker run -d --name ov-a --network ov-lab alpine:3.20 sleep 300
   COMMAND: docker run -d --name ov-b --network ov-lab alpine:3.20 sleep 300
4. Prove reachability and inspect overlay metadata.
   COMMAND: docker exec ov-a ping -c1 ov-b
   COMMAND: docker network inspect ov-lab

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove overlay resources: docker rm -f ov-a ov-b 2>/dev/null || true; docker network rm ov-lab 2>/dev/null || true; docker swarm leave --force 2>/dev/null || true

## Concept Check
- Which inspect field proves this is an overlay network and not a local bridge?
- What control-plane dependency would you suspect first if name resolution works but remote endpoints fail?
- Which additional data-plane signal would you collect on a real multi-node outage?

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
