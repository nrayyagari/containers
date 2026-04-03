# Tmpfs Mounts Lab

## Goal
Develop hands-on confidence for Tmpfs Mounts and prove understanding through observable output.

## Prerequisites
- Docker Engine on Linux and permission to use tmpfs mounts.
- Enough RAM available for a small in-memory mount.
- Permission to run commands for this module.

## Steps
1. Run a container with a tmpfs mount.
   COMMAND: docker run -d --name tmpfs-lab --mount type=tmpfs,dst=/cache,tmpfs-size=67108864 alpine:3.20 sleep 300
2. Prove the mount type and write an ephemeral file.
   COMMAND: docker exec tmpfs-lab sh -c "mount | grep /cache && echo hot-data >/cache/proof.txt && ls -l /cache"
3. Recreate the container with the same tmpfs mount.
   COMMAND: docker rm -f tmpfs-lab
   COMMAND: docker run -d --name tmpfs-lab --mount type=tmpfs,dst=/cache,tmpfs-size=67108864 alpine:3.20 sleep 300
4. Confirm the file is gone after recreation.
   COMMAND: docker exec tmpfs-lab ls -l /cache

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the tmpfs test container: docker rm -f tmpfs-lab 2>/dev/null || true

## Concept Check
- Which command output proves the data lived in memory-backed storage rather than a persistent volume?
- What production trade-off makes tmpfs attractive for secrets or scratch space but dangerous for durable state?
- Why is recreating the container a stronger persistence test than simply restarting the process inside it?

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
