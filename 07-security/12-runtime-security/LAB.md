# Runtime Security Lab

## Goal
Develop hands-on confidence for Runtime Security and prove understanding through observable output.

## Prerequisites
- Falco, Tracee, or another runtime detector installed and collecting events.
- Access to the detector output source, such as `journalctl` or Kubernetes logs.
- Permission to run commands for this module.

## Steps
1. Start a disposable workload container.
   COMMAND: docker run -d --name runtime-lab alpine:3.20 sleep 300
2. Trigger activity that a runtime detector should make visible.
   COMMAND: docker exec runtime-lab sh -c "id && touch /etc/runtime-proof"
3. Inspect recent detector output.
   COMMAND: journalctl -u falco --since "5 minutes ago" --no-pager | tail -n 50 || true
   COMMAND: kubectl logs -n falco ds/falco --tail=50 || true
4. Explain which signal, rule, or event would justify containment action first.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control, privilege boundary, or verification result.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the runtime-security test container: docker rm -f runtime-lab 2>/dev/null || true

## Concept Check
- Which signal tells you a detector is observing real runtime behavior instead of only static configuration?
- Why is runtime security still necessary after scanning, signing, and least-privilege hardening?
- What is the first containment action you would take if the detector reported truly suspicious activity in production?

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
