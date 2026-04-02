# Tags Lab

## Goal
Develop hands-on confidence for Tags and prove understanding through observable output.

## Prerequisites
- Non-production test environment with required tools.
- Permission to run commands for this module.

## Steps
1. Prepare deterministic build context under /tmp.
2. Build image for this topic.
   COMMAND: docker build -t img-lab:latest /tmp/img-lab
3. Run resulting image and verify behavior.
   COMMAND: docker run --rm img-lab:latest
4. Inspect layer history and record one optimization.
   COMMAND: docker history img-lab:latest

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control/mechanism.
- You can relate the output to one production risk.

## Verify
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

## Cleanup
- Remove images and temp files: docker rmi img-lab:latest 2>/dev/null || true; rm -rf /tmp/img-lab /tmp/dbk-lab

## Concept Check
- Which artifact identity signal in this lab is strongest for release safety?
- What drift risk appears when relying on mutable tags only?
- Which release rule should require digest evidence before deploy?

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
