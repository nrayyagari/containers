# Docker Proxy Lab

## Goal
Develop hands-on confidence for Docker Proxy and prove understanding through observable output.

## Prerequisites
- Linux host with Docker Engine, `ss`, `pgrep`, and `iptables` available.
- Host port `8089` available for the test.
- Permission to run commands for this module.

## Steps
1. Run a container with a localhost-only published port.
   COMMAND: docker run -d --name proxy-lab -p 127.0.0.1:8089:80 nginx:1.27-alpine
2. Check whether a `docker-proxy` process exists on this host.
   COMMAND: pgrep -a docker-proxy || true
3. Inspect the host listener and NAT rule for the published port.
   COMMAND: ss -ltnp | grep ':8089 ' || true
   COMMAND: iptables -t nat -S | grep 8089 || true
4. Record whether this engine relied on userland proxying, kernel NAT, or both.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the proxy lab container: docker rm -f proxy-lab 2>/dev/null || true

## Concept Check
- Which evidence distinguished a userland proxy process from a pure NAT path?
- What daemon setting or kernel behavior can change the result across hosts?
- Why do loopback-published ports often expose proxy behavior before other traffic paths do?

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
