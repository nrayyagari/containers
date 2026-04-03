# Backup and Restore Lab

## Goal
Develop hands-on confidence for Backup and Restore and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to create volumes and write under `/tmp`.
- No production data should share the temporary backup paths.
- Permission to run commands for this module.

## Steps
1. Create a source volume with sample data.
   COMMAND: docker volume create backup-src
   COMMAND: docker run --rm -v backup-src:/data alpine:3.20 sh -c "echo backup-me >/data/proof.txt"
2. Create a tarball backup using a helper container.
   COMMAND: mkdir -p /tmp/backup-lab
   COMMAND: docker run --rm -v backup-src:/data -v /tmp/backup-lab:/backup alpine:3.20 tar czf /backup/data.tgz -C /data .
3. Restore the backup into a new volume.
   COMMAND: docker volume create backup-dst
   COMMAND: docker run --rm -v backup-dst:/data -v /tmp/backup-lab:/backup alpine:3.20 sh -c "tar xzf /backup/data.tgz -C /data && cat /data/proof.txt"
4. Inspect the restored volume and confirm the expected files exist.
   COMMAND: docker run --rm -v backup-dst:/data alpine:3.20 ls -l /data

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove backup lab resources: docker volume rm backup-src backup-dst 2>/dev/null || true; rm -rf /tmp/backup-lab

## Concept Check
- Which step proves the backup artifact is independent from the original running container?
- What failure mode appears if you back up container state without testing restore semantics?
- Why is a restore test more valuable than a backup job that only reports success?

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
