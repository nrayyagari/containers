# Drop Capabilities Lab

## Goal
Develop hands-on confidence for Drop Capabilities and prove understanding through observable output.

## Prerequisites
- Docker Engine on Linux with ability to run basic Alpine containers.
- No security policy should block the test container creation.
- Permission to run commands for this module.

## Steps
1. Record the baseline effective capability bitmap.
   COMMAND: docker run --rm alpine:3.20 sh -c "grep CapEff /proc/self/status"
2. Drop all capabilities and attempt a raw-socket operation.
   COMMAND: docker run --rm --cap-drop ALL alpine:3.20 ping -c1 127.0.0.1 || true
3. Add back only `NET_RAW` and retry the same operation.
   COMMAND: docker run --rm --cap-drop ALL --cap-add NET_RAW alpine:3.20 ping -c1 127.0.0.1
4. Explain why `--privileged` would be an excessive fix for this exact failure.

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
- Which step proves capability removal changed the outcome rather than application configuration?
- Why is adding back one capability safer than leaving the container at the default capability set blindly?
- What other Linux control should you inspect if the narrowed capability set still feels too broad?

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
