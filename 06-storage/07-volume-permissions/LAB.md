# Volume Permissions Lab

## Goal
Develop hands-on confidence for Volume Permissions and prove understanding through observable output.

## Prerequisites
- Linux host with Docker Engine.
- Permission to change ownership on a disposable host directory.
- Permission to run commands for this module.

## Steps
1. Prepare a restrictive host directory.
   COMMAND: rm -rf /tmp/perm-lab
   COMMAND: mkdir -p /tmp/perm-lab
   COMMAND: chmod 700 /tmp/perm-lab
   COMMAND: chown root:root /tmp/perm-lab
2. Attempt a write as a non-root container user and observe the failure.
   COMMAND: docker run --rm --user 1000:1000 -v /tmp/perm-lab:/data alpine:3.20 sh -c "id && echo fail >/data/proof.txt" || true
3. Fix ownership alignment and retry the write.
   COMMAND: chown 1000:1000 /tmp/perm-lab
   COMMAND: docker run --rm --user 1000:1000 -v /tmp/perm-lab:/data alpine:3.20 sh -c "echo success >/data/proof.txt && ls -ln /data"
4. Inspect host ownership to prove the UID and GID mapping outcome.
   COMMAND: ls -ln /tmp/perm-lab

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the permissions lab directory: rm -rf /tmp/perm-lab

## Concept Check
- Which output proves this was a filesystem permission problem rather than a Docker storage problem?
- Why does matching the container UID/GID to the backend path matter more than the username string?
- What is the first thing you would inspect when a stateful container starts but cannot write its data path?

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
