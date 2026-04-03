# Image Scanning Lab

## Goal
Develop hands-on confidence for Image Scanning and prove understanding through observable output.

## Prerequisites
- Trivy or an equivalent container image scanner installed.
- Internet access available for image pull and vulnerability database refresh.
- Permission to run commands for this module.

## Steps
1. Pull a representative image for scanning.
   COMMAND: docker pull python:3.12-slim
2. Scan the image for high and critical findings.
   COMMAND: trivy image --severity HIGH,CRITICAL python:3.12-slim
3. Inspect the image digest you actually scanned.
   COMMAND: docker image inspect python:3.12-slim --format "{{index .RepoDigests 0}}"
4. Record one finding that materially affects risk and one that needs contextual triage.

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
- Which output proves the scan applied to a specific image digest rather than a mutable tag alone?
- Why is a vulnerability list not the same thing as exploitability or runtime risk?
- What extra context do you need before blocking a deployment on scanner output?

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
