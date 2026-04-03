# User Namespace Mapping Lab

## Goal
Develop hands-on confidence for User Namespace Mapping and prove understanding through observable output.

## Prerequisites
- Docker Engine configured with `userns-remap` or another user-namespace-aware mode for full effect.
- Access to `/etc/subuid` and `/etc/subgid` on the host.
- Permission to run commands for this module.

## Steps
1. Inspect Docker security options and subordinate ID mappings.
   COMMAND: docker info --format "{{json .SecurityOptions}}"
   COMMAND: grep -E "^(dockremap|[^:]+):" /etc/subuid /etc/subgid | head -n 10 || true
2. Prepare a bind-mounted workspace.
   COMMAND: rm -rf /tmp/userns-lab
   COMMAND: mkdir -p /tmp/userns-lab
3. Write a file from container root into the bind mount.
   COMMAND: docker run --rm -v /tmp/userns-lab:/data alpine:3.20 sh -c "id && echo mapped >/data/proof.txt"
4. Inspect host-side ownership and explain whether root was remapped.
   COMMAND: ls -ln /tmp/userns-lab/proof.txt

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control, privilege boundary, or verification result.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the user namespace lab directory: rm -rf /tmp/userns-lab

## Concept Check
- Which host UID and GID values prove container root was or was not remapped?
- Why do bind mounts become more operationally complex once user namespace remapping is enabled?
- How is this control different from running the whole daemon in rootless mode?

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
