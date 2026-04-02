# Namespaces Deep Dive Lab

## Goal
Develop hands-on confidence for Namespaces Deep Dive and prove understanding through observable output.

## Prerequisites
- Non-production test environment with required tools.
- Permission to run commands for this module.

## Steps
1. Start container for namespace inspection.
   COMMAND: docker run -d --name ns-lab alpine:3.20 sleep 300
2. Compare process views.
   COMMAND: ps -ef | head -n 10
   COMMAND: docker exec ns-lab ps -ef
3. Compare namespace links from host PID.
   COMMAND: pid=$(docker inspect -f '{{.State.Pid}}' ns-lab); ls -l /proc/$pid/ns

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
- Which output line is your strongest proof for this topic?
- What breaks in production if this concept is misunderstood?
- What are your first two diagnostic commands during incident response?

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
