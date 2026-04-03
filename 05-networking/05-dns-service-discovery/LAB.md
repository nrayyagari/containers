# DNS and Service Discovery Lab

## Goal
Develop hands-on confidence for DNS and Service Discovery and prove understanding through observable output.

## Prerequisites
- Docker Engine and a user-defined network available for test containers.
- BusyBox image pull permitted from your test environment.
- Permission to run commands for this module.

## Steps
1. Create an isolated network for service discovery.
   COMMAND: docker network create dns-lab
2. Start one service container and one client container.
   COMMAND: docker run -d --name dns-svc --network dns-lab busybox:1.36 sleep 300
   COMMAND: docker run -d --name dns-cli --network dns-lab busybox:1.36 sleep 300
3. Resolve the service by container name and inspect the resolver configuration.
   COMMAND: docker exec dns-cli nslookup dns-svc
   COMMAND: docker exec dns-cli cat /etc/resolv.conf
4. Reconnect the service with an alias and resolve the alias.
   COMMAND: docker network disconnect dns-lab dns-svc
   COMMAND: docker network connect --alias api dns-lab dns-svc
   COMMAND: docker exec dns-cli nslookup api

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove DNS lab resources: docker rm -f dns-svc dns-cli 2>/dev/null || true; docker network rm dns-lab 2>/dev/null || true

## Concept Check
- Which line proves Docker DNS is answering inside the network namespace?
- What breaks differently when the issue is DNS resolution versus transport reachability?
- Why are aliases safer than hard-coded IP addresses in ephemeral container environments?

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
