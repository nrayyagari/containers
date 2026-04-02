# Linux Capabilities Lab

## Goal
Develop hands-on confidence for Linux Capabilities and prove understanding through observable output.

## Prerequisites
- Non-production test environment with required tools.
- Permission to run commands for this module.

## Steps
1. Run with all capabilities dropped.
   COMMAND: docker run --rm --cap-drop ALL alpine:3.20 sh -c "id && ping -c1 127.0.0.1 || true"
2. Re-run with minimum add-back.
   COMMAND: docker run --rm --cap-drop ALL --cap-add NET_RAW alpine:3.20 ping -c1 127.0.0.1
3. Compare output and identify why behavior changed.

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
- Which command result proved capability-based least privilege in practice?
- Why is add-only-required capability safer than default capability set?
- What incident class becomes more likely when excessive capabilities are allowed?

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
