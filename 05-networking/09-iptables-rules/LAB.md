# Iptables Rules Lab

## Goal
Develop hands-on confidence for Iptables Rules and prove understanding through observable output.

## Prerequisites
- Linux host with root-level access to `iptables` or `iptables-save`.
- Docker Engine and host port `8090` available.
- Permission to run commands for this module.

## Steps
1. Create a dedicated bridge and publish a web container on it.
   COMMAND: docker network create fw-lab
   COMMAND: docker run -d --name fw-web --network fw-lab -p 8090:80 nginx:1.27-alpine
2. Inspect the Docker-managed filter chains.
   COMMAND: iptables -S DOCKER || true
   COMMAND: iptables -S DOCKER-USER || true
3. Inspect the NAT rules for the published port.
   COMMAND: iptables -t nat -S | grep 8090 || true
4. Capture the container IP and explain the packet path from `8090` to that endpoint.
   COMMAND: docker inspect fw-web --format '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}'

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove firewall lab resources: docker rm -f fw-web 2>/dev/null || true; docker network rm fw-lab 2>/dev/null || true

## Concept Check
- Which chain would you change first if you wanted to add policy without breaking Docker's own rules?
- What symptom tells you the packet is being dropped before it reaches the container rather than by the app?
- Why is reading the actual ruleset safer than assuming the default Docker behavior is still intact?

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
