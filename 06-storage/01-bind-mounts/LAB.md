# Bind Mounts Lab

## Goal
Develop hands-on confidence for Bind Mounts and prove understanding through observable output.

## Prerequisites
- Non-production Linux host with Docker Engine.
- Host path `/tmp` available for disposable test data.
- Permission to run commands for this module.

## Steps
1. Prepare a host directory and seed file.
   COMMAND: mkdir -p /tmp/bind-lab
   COMMAND: echo host-data >/tmp/bind-lab/proof.txt
2. Mount the host path into a container and read it from inside the container.
   COMMAND: docker run --rm --name bind-lab -v /tmp/bind-lab:/data alpine:3.20 cat /data/proof.txt
3. Write from the container and confirm the change is visible on the host.
   COMMAND: docker run --rm -v /tmp/bind-lab:/data alpine:3.20 sh -c "echo container-write >> /data/proof.txt"
   COMMAND: cat /tmp/bind-lab/proof.txt
4. Repeat the mount as read-only and observe the write failure.
   COMMAND: docker run --rm -v /tmp/bind-lab:/data:ro alpine:3.20 sh -c "echo fail >> /data/proof.txt" || true

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove bind-mount test data: rm -rf /tmp/bind-lab

## Concept Check
- Which output proves the container is operating directly on a host path instead of Docker-managed storage?
- What risk appears immediately if you bind-mount sensitive host paths into a writable container?
- Why is a bind mount often the right choice for local development but not for portable production state?

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
