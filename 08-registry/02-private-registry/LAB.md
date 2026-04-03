# Private Registry Lab

## Goal
Develop hands-on confidence for Private Registry and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to run a disposable registry container.
- If your engine does not allow plain HTTP to `localhost` by default, configure local insecure-registry access for the lab port.
- Permission to run commands for this module.

## Steps
1. Start a local private registry.
   COMMAND: docker run -d -p 5000:5000 --name reg-lab registry:3
2. Tag and push a test image into the registry.
   COMMAND: docker pull alpine:3.20
   COMMAND: docker tag alpine:3.20 localhost:5000/private-lab:1
   COMMAND: docker push localhost:5000/private-lab:1
3. Inspect the catalog exposed by the registry API.
   COMMAND: curl -s http://localhost:5000/v2/_catalog | jq
4. Pull the image back from the private registry and record its digest.
   COMMAND: docker pull localhost:5000/private-lab:1
   COMMAND: docker image inspect localhost:5000/private-lab:1 --format "{{index .RepoDigests 0}}"

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the private registry lab container: docker rm -f reg-lab 2>/dev/null || true

## Concept Check
- Which output proves the registry is the system of record for the pushed artifact rather than your local image cache?
- What control or compliance need usually drives organizations to a private registry instead of only Docker Hub?
- Why should you validate registry API state instead of trusting a successful push message alone?

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
