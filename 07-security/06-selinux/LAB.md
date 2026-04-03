# SELinux Lab

## Goal
Develop hands-on confidence for SELinux and prove understanding through observable output.

## Prerequisites
- SELinux-enabled host, ideally in `Enforcing` mode.
- Host tools `getenforce` and `ls -Z` available.
- Permission to run commands for this module.

## Steps
1. Create a disposable host directory and inspect its initial SELinux label.
   COMMAND: rm -rf /tmp/selinux-lab
   COMMAND: mkdir -p /tmp/selinux-lab
   COMMAND: getenforce
   COMMAND: ls -Zd /tmp/selinux-lab
2. Mount the path with relabeling and write a file from the container.
   COMMAND: docker run --rm -v /tmp/selinux-lab:/data:Z alpine:3.20 sh -c "echo selinux >/data/proof.txt"
3. Inspect the resulting directory and file labels.
   COMMAND: ls -Zd /tmp/selinux-lab
   COMMAND: ls -Z /tmp/selinux-lab/proof.txt
4. Explain why `:Z` or `:z` changes access outcomes on enforcing hosts.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control, privilege boundary, or verification result.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the SELinux lab directory: rm -rf /tmp/selinux-lab

## Concept Check
- Which output proves the host path label changed to permit container access?
- Why can a bind mount look correct at the Unix permission layer but still fail under SELinux?
- What is the safest first troubleshooting step before disabling SELinux enforcement?

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
