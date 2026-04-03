# AppArmor Profiles Lab

## Goal
Develop hands-on confidence for AppArmor Profiles and prove understanding through observable output.

## Prerequisites
- Linux host with AppArmor enabled.
- `aa-status` available on the host for profile inspection.
- Permission to run commands for this module.

## Steps
1. Verify that AppArmor is active on the host.
   COMMAND: aa-status | sed -n "1,20p" || true
2. Run a default container and inspect the attached AppArmor label.
   COMMAND: docker run --rm alpine:3.20 cat /proc/self/attr/current || true
3. Run explicitly with the default Docker profile and compare the label.
   COMMAND: docker run --rm --security-opt apparmor=docker-default alpine:3.20 cat /proc/self/attr/current || true
4. Inspect recent AppArmor audit lines after the test.
   COMMAND: dmesg | grep -i apparmor | tail -n 20 || true

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
- Which line proves an AppArmor profile was attached to the container process?
- How do AppArmor audit messages help you narrow a deny rule without loosening everything?
- Why is AppArmor complementary to seccomp rather than a replacement for it?

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
