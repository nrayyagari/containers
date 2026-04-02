# Docker Daemon Lab

## Goal
Develop hands-on confidence for Docker Daemon and prove understanding through observable output.

## Prerequisites
- Non-production test environment with required tools.
- Permission to run commands for this module.

## Steps
1. Pull base image.
   COMMAND: docker pull alpine:3.20
2. Start and inspect container.
   COMMAND: docker run -d --name dk-lab alpine:3.20 sleep 300
   COMMAND: docker inspect dk-lab --format "{{.Config.Image}} {{.State.Status}}"
3. Execute command inside running container.
   COMMAND: docker exec dk-lab sh -c "id && hostname"

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control/mechanism.
- You can relate the output to one production risk.

## Verify
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

## Cleanup
- Remove resources: docker rm -f dk-lab net-a net-b 2>/dev/null || true; docker volume rm vol-lab 2>/dev/null || true; docker network rm net-lab 2>/dev/null || true

## Concept Check
- Which daemon/runtime signal is most useful when container starts fail?
- What platform risk appears from unsafe daemon configuration defaults?
- Which diagnostic command should be first for daemon-level incidents?

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
