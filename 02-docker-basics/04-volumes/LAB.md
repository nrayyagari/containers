# Volumes Lab

## Goal
Develop hands-on confidence for Volumes and prove understanding through observable output.

## Prerequisites
- Non-production test environment with required tools.
- Permission to run commands for this module.

## Steps
1. Create named volume.
   COMMAND: docker volume create vol-lab
2. Write data through container.
   COMMAND: docker run --rm -v vol-lab:/data alpine:3.20 sh -c "echo persisted > /data/value.txt"
3. Read data from new container and verify persistence.
   COMMAND: docker run --rm -v vol-lab:/data alpine:3.20 cat /data/value.txt

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control/mechanism.
- You can relate the output to one production risk.

## Verify
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

## Cleanup
- Remove resources: docker rm -f dk-lab net-a net-b 2>/dev/null || true; docker volume rm vol-lab 2>/dev/null || true; docker network rm net-lab 2>/dev/null || true

## Concept Check
- Which output proves data persistence across container lifecycle?
- What data-loss scenario appears if teams store state only in writable layers?
- Which backup/restore check should accompany volume adoption?

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
