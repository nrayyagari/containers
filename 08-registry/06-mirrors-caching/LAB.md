# Mirrors and Caching Lab

## Goal
Develop hands-on confidence for Mirrors and Caching and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to run a disposable registry mirror.
- If your engine does not allow plain HTTP to `localhost` by default, configure local insecure-registry access for the lab port.
- Permission to run commands for this module.

## Steps
1. Create a pull-through cache configuration.
   COMMAND: rm -rf /tmp/mirror-lab
   COMMAND: mkdir -p /tmp/mirror-lab
   COMMAND: printf '%s\n' 'version: 0.1' 'proxy:' '  remoteurl: https://registry-1.docker.io' 'storage:' '  filesystem:' '    rootdirectory: /var/lib/registry' > /tmp/mirror-lab/config.yml
2. Start the mirror registry.
   COMMAND: docker run -d --name mirror-reg -p 5003:5000 -v /tmp/mirror-lab/config.yml:/etc/distribution/config.yml registry:3
3. Pull the same image through the mirror twice.
   COMMAND: docker pull localhost:5003/library/alpine:3.20
   COMMAND: docker pull localhost:5003/library/alpine:3.20
4. Inspect mirror logs and explain the initial fetch versus cached behavior.
   COMMAND: docker logs mirror-reg | tail -n 30

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove mirror lab resources: docker rm -f mirror-reg 2>/dev/null || true; rm -rf /tmp/mirror-lab

## Concept Check
- Which evidence distinguishes a first-time upstream fetch from a subsequent cache hit?
- What outage or latency risk does a local mirror reduce in real environments?
- Why should you still treat the mirror as part of the supply chain instead of as a transparent network optimization?

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
