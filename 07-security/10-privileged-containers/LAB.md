# Privileged Containers Lab

## Goal
Develop hands-on confidence for Privileged Containers and prove understanding through observable output.

## Prerequisites
- Docker Engine on Linux with permission to run privileged containers in a disposable environment.
- Do not run this on a production host.
- Permission to run commands for this module.

## Steps
1. Attempt a privileged operation in a normal container and observe the failure.
   COMMAND: docker run --rm alpine:3.20 sh -c "mkdir /mnt && mount -t tmpfs tmpfs /mnt" || true
2. Repeat the operation in a privileged container.
   COMMAND: docker run --rm --privileged alpine:3.20 sh -c "mkdir /mnt && mount -t tmpfs tmpfs /mnt && mount | grep /mnt"
3. Compare the effective capability bitmaps.
   COMMAND: docker run --rm alpine:3.20 sh -c "grep CapEff /proc/self/status"
   COMMAND: docker run --rm --privileged alpine:3.20 sh -c "grep CapEff /proc/self/status"
4. Explain why this flag is effectively a near-host trust decision.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control, privilege boundary, or verification result.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- No persistent cleanup is required for this lab.

## Concept Check
- Which result proves `--privileged` granted far more power than the original workload actually needed?
- What blast-radius increase appears the moment a container can mount filesystems or manipulate the host more freely?
- Why is `--privileged` usually a design smell rather than a normal troubleshooting step?

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
