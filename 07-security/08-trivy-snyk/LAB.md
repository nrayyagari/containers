# Trivy and Snyk Lab

## Goal
Develop hands-on confidence for Trivy and Snyk and prove understanding through observable output.

## Prerequisites
- Both Trivy and Snyk installed, with Snyk authenticated if required by your setup.
- `jq` available for lightweight JSON inspection.
- Permission to run commands for this module.

## Steps
1. Pull a common image for side-by-side scanning.
   COMMAND: docker pull python:3.12-slim
2. Scan the image with Trivy and save JSON output.
   COMMAND: trivy image --format json -o /tmp/trivy-lab.json python:3.12-slim
3. Scan the same image with Snyk and save JSON output.
   COMMAND: snyk container test python:3.12-slim --json-file-output=/tmp/snyk-lab.json || true
4. Inspect the two outputs and note workflow or finding differences.
   COMMAND: jq ".Results[0] // ." /tmp/trivy-lab.json | head -n 20
   COMMAND: jq ".vulnerabilities // ." /tmp/snyk-lab.json | head -n 20 || true

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control, privilege boundary, or verification result.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove comparison artifacts: rm -f /tmp/trivy-lab.json /tmp/snyk-lab.json

## Concept Check
- Which difference came from the tool workflow or data model rather than a real change in the image?
- Why should CI policy define normalization rules before comparing scanner results?
- What does this exercise teach you about using multiple scanners without creating alert fatigue?

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
