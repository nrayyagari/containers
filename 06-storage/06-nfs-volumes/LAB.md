# NFS Volumes Lab

## Goal
Develop hands-on confidence for NFS Volumes and prove understanding through observable output.

## Prerequisites
- Reachable NFSv4 server and export path for non-production testing.
- Host tools and kernel support required for NFS mounts.
- Permission to run commands for this module.

## Steps
1. Export the NFS endpoint details for the lab.
   COMMAND: export NFS_SERVER=192.0.2.10
   COMMAND: export NFS_EXPORT=/exports/containers
2. Create an NFS-backed Docker volume.
   COMMAND: docker volume create --driver local --opt type=nfs --opt o=addr=${NFS_SERVER},nfsvers=4,rw --opt device=:${NFS_EXPORT} nfs-lab
3. Mount the NFS volume in a container and write a proof file.
   COMMAND: docker run --rm -v nfs-lab:/data alpine:3.20 sh -c "echo shared >/data/proof.txt && ls -l /data"
4. Inspect the volume definition and, if you can reach the server, verify the file exists on the export.
   COMMAND: docker volume inspect nfs-lab

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the NFS volume definition: docker volume rm nfs-lab 2>/dev/null || true

## Concept Check
- Which configuration value proves the container is writing to remote storage instead of host-local storage?
- What additional failure modes appear with NFS around latency, locking, or server availability?
- Why should you prove server-side visibility before assuming a restart-safe persistence model?

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
