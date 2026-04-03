# Rootless Containers Lab

## Goal
Develop hands-on confidence for Rootless Containers and prove understanding through observable output.

## Prerequisites
- Rootless Docker installed and available to the current user if you want full runtime proof.
- Systemd user services or equivalent user-session tooling available on the host.
- Permission to run commands for this module.

## Steps
1. Check rootless prerequisites and setup status.
   COMMAND: dockerd-rootless-setuptool.sh check || true
2. Inspect the user-level Docker service if present.
   COMMAND: systemctl --user status docker --no-pager || true
3. Inspect Docker security options for rootless indicators.
   COMMAND: docker info --format "{{json .SecurityOptions}}"
4. Record the daemon-related processes owned by the current user.
   COMMAND: ps -ef | grep -E "dockerd|rootlesskit" | grep -v grep || true

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control, privilege boundary, or verification result.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- No persistent cleanup is required for this inspection-oriented lab.

## Concept Check
- Which output proves the daemon and helper processes are not running as root?
- What capability or networking limitations should you expect to differ in rootless mode?
- Why does rootless mode reduce daemon blast radius even when the container image itself is unchanged?

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
