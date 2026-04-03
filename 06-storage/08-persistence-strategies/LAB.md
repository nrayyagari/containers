# Persistence Strategies Lab

## Goal
Develop hands-on confidence for Persistence Strategies and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to create named volumes.
- No production container should use the temporary resource names.
- Permission to run commands for this module.

## Steps
1. Write data only into a container writable layer.
   COMMAND: docker run --name ephem-lab alpine:3.20 sh -c "mkdir -p /state && echo ephemeral >/state/proof.txt"
2. Replace the container and show the writable-layer data is gone.
   COMMAND: docker rm ephem-lab
   COMMAND: docker run --rm --name ephem-lab alpine:3.20 sh -c "cat /state/proof.txt" || true
3. Write equivalent data into a named volume.
   COMMAND: docker volume create persist-lab
   COMMAND: docker run --rm -v persist-lab:/state alpine:3.20 sh -c "echo durable >/state/proof.txt"
4. Mount the volume in a new container and confirm the data persists.
   COMMAND: docker run --rm -v persist-lab:/state alpine:3.20 cat /state/proof.txt

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove persistence lab resources: docker volume rm persist-lab 2>/dev/null || true

## Concept Check
- Which observation proves the restart-safe data path was externalized from the container lifecycle?
- What design mistake causes teams to lose state during normal redeployments?
- Why should you decide explicitly which data is ephemeral and which data is durable before writing the container spec?

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
