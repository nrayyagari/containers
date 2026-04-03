# Security Best Practices Lab

## Goal
Develop hands-on confidence for Security Best Practices and prove understanding through observable output.

## Prerequisites
- Docker Engine on Linux.
- No production workload should use the temporary container names.
- Permission to run commands for this module.

## Steps
1. Run a baseline container with default runtime settings.
   COMMAND: docker run -d --name sec-base alpine:3.20 sleep 300
2. Run a hardened container with a narrower runtime profile.
   COMMAND: docker run -d --name sec-hard --read-only --cap-drop ALL --security-opt no-new-privileges --pids-limit 64 --tmpfs /tmp alpine:3.20 sleep 300
3. Compare the two security-relevant host configs.
   COMMAND: docker inspect sec-base --format "Privileged={{.HostConfig.Privileged}} Readonly={{.HostConfig.ReadonlyRootfs}} PidsLimit={{.HostConfig.PidsLimit}} SecurityOpt={{json .HostConfig.SecurityOpt}}"
   COMMAND: docker inspect sec-hard --format "Privileged={{.HostConfig.Privileged}} Readonly={{.HostConfig.ReadonlyRootfs}} PidsLimit={{.HostConfig.PidsLimit}} SecurityOpt={{json .HostConfig.SecurityOpt}}"
4. Prove the hardened container blocks root filesystem writes but still allows the intended tmpfs scratch path.
   COMMAND: docker exec sec-hard sh -c "touch /root/should-fail" || true
   COMMAND: docker exec sec-hard sh -c "touch /tmp/ok && ls -l /tmp/ok"

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control, privilege boundary, or verification result.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the security best-practices test containers: docker rm -f sec-base sec-hard 2>/dev/null || true

## Concept Check
- Which runtime flags delivered the biggest security improvement for the least operational cost?
- Why is defense in depth stronger than relying on a single control such as scanning or signing?
- How would you phase these controls into an existing workload without causing an avoidable outage?

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
