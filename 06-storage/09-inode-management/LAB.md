# Inode Management Lab

## Goal
Develop hands-on confidence for Inode Management and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to create test volumes.
- Enough disk and inode headroom for a small-file exercise.
- Permission to run commands for this module.

## Steps
1. Create a test volume and capture its initial inode view.
   COMMAND: docker volume create inode-lab
   COMMAND: docker run --rm -v inode-lab:/data alpine:3.20 df -i /data
2. Create many small files inside the volume.
   COMMAND: docker run --rm -v inode-lab:/data alpine:3.20 sh -c "for i in $(seq 1 5000); do touch /data/f${i}; done; ls /data | wc -l"
3. Compare byte consumption and inode consumption.
   COMMAND: docker run --rm -v inode-lab:/data alpine:3.20 sh -c "df -h /data && df -i /data"
4. Explain why a node can still reject writes even if `df -h` looks healthy.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the inode lab volume: docker volume rm inode-lab 2>/dev/null || true

## Concept Check
- Which command output proves inode pressure is a separate resource limit from bytes on disk?
- What workload pattern is most likely to hit inode exhaustion first?
- Why should incident triage check `df -i` alongside `df -h` for storage-related failures?

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
