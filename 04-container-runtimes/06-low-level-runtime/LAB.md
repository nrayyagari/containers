# Low Level Runtime Lab

## Goal
Develop hands-on confidence for Low Level Runtime and prove understanding through observable output.

## Prerequisites
- Non-production test environment with required tools.
- Permission to run commands for this module.

## Steps
1. Collect runtime process baseline.
   COMMAND: ps -ef | grep -E "containerd|shim|runc" | grep -v grep | head -n 30
2. Start container and capture PID linkage.
   COMMAND: docker run -d --name rt-lab alpine:3.20 sleep 300
   COMMAND: docker inspect rt-lab --format "{{.Id}} {{.State.Pid}}"
3. Map observed processes to runtime layers.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control/mechanism.
- You can relate the output to one production risk.

## Verify
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

## Cleanup
- Remove runtime test container: docker rm -f rt-lab 2>/dev/null || true

## Concept Check
- Which process or metadata evidence proves low-level runtime execution path?
- What breaks when OCI/runtime assumptions differ across environments?
- Which first command confirms runtime layer ownership of failure?

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
