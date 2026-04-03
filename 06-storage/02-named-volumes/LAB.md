# Named Volumes Lab

## Goal
Develop hands-on confidence for Named Volumes and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to create and inspect volumes.
- No production container should be using the test volume name.
- Permission to run commands for this module.

## Steps
1. Create a named volume and write data into it.
   COMMAND: docker volume create vol-lab
   COMMAND: docker run --rm -v vol-lab:/data alpine:3.20 sh -c "echo durable >/data/proof.txt"
2. Inspect the volume metadata and mountpoint.
   COMMAND: docker volume inspect vol-lab
3. Mount the same volume in a new container and prove the data persisted.
   COMMAND: docker run --rm -v vol-lab:/data alpine:3.20 cat /data/proof.txt
4. Explain why this survived container replacement but writable-layer data would not.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the named volume: docker volume rm vol-lab 2>/dev/null || true

## Concept Check
- Which field shows Docker, not the container, owns the volume lifecycle?
- What failure mode appears when teams treat a named volume like image content or container state?
- Why is inspecting the mountpoint more trustworthy than assuming persistence from a successful write?

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
