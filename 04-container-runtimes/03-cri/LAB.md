# Cri Lab

## Goal
Develop hands-on confidence for Cri and prove understanding through observable output.

## Prerequisites
- Non-production test environment with required tools.
- Permission to run commands for this module.

## Steps
1. Inspect runtime service status.
   COMMAND: systemctl status containerd --no-pager || true
2. Collect CRI view when available.
   COMMAND: crictl info || true
   COMMAND: crictl ps -a || true
3. Compare with Docker view and identify operational source of truth.
   COMMAND: docker ps -a || true

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
- Which command output is authoritative for kubelet-managed runtime state?
- What node failure mode appears when CRI endpoint/runtime alignment is broken?
- Which diagnostic sequence should precede any runtime restart action?

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
