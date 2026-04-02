# Process Isolation Lab

## Goal
Develop hands-on confidence for Process Isolation and prove understanding through observable output.

## Prerequisites
- Non-production test environment with required tools.
- Permission to run commands for this module.

## Steps
1. Start reference container.
   COMMAND: docker run -d --name fnd-lab alpine:3.20 sleep 300
2. Collect process and status evidence.
   COMMAND: docker inspect fnd-lab --format "{{.State.Pid}} {{.State.Status}}"
   COMMAND: docker exec fnd-lab cat /proc/1/status | sed -n '1,25p'
3. Record one isolation boundary and one shared resource.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control/mechanism.
- You can relate the output to one production risk.

## Verify
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

## Cleanup
- Remove containers: docker rm -f fnd-lab ns-lab cg-lab sec-lab 2>/dev/null || true

## Concept Check
- Which process-tree evidence proves container process isolation?
- How can host PID assumptions cause incorrect incident conclusions?
- What first check separates container crash from host-level process issue?

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
