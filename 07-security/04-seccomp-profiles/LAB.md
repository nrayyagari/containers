# Seccomp Profiles Lab

## Goal
Develop hands-on confidence for Seccomp Profiles and prove understanding through observable output.

## Prerequisites
- Docker Engine on Linux with outbound package access from the test container.
- Permission to run containers with custom security options.
- Permission to run commands for this module.

## Steps
1. Run a syscall pattern that is commonly blocked by the default seccomp profile.
   COMMAND: docker run --rm alpine:3.20 sh -c "apk add --no-cache util-linux >/dev/null && unshare -Ur true" || true
2. Repeat the test with seccomp disabled for the container.
   COMMAND: docker run --rm --security-opt seccomp=unconfined alpine:3.20 sh -c "apk add --no-cache util-linux >/dev/null && unshare -Ur true"
3. Inspect seccomp mode from inside a default container.
   COMMAND: docker run --rm alpine:3.20 sh -c "grep Seccomp /proc/self/status"
4. Record which syscall boundary changed and why that matters operationally.

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
- Which result shows a syscall filter blocked the action rather than the filesystem or capability layer?
- Why should you change seccomp policy narrowly instead of defaulting to `unconfined`?
- What is the first proof signal you would collect if a workload starts failing only after a seccomp hardening change?

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
