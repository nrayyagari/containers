# IPv6 Lab

## Goal
Develop hands-on confidence for IPv6 and prove understanding through observable output.

## Prerequisites
- Docker daemon configured with IPv6 enabled.
- Linux host and BusyBox image available for test containers.
- Permission to run commands for this module.

## Steps
1. Create a dual-stack user-defined network.
   COMMAND: docker network create --ipv6 --subnet 172.28.0.0/16 --subnet fd42:dead:beef::/64 ip6-lab
2. Start two containers on the IPv6-capable network.
   COMMAND: docker run -d --name ip6-a --network ip6-lab busybox:1.36 sleep 300
   COMMAND: docker run -d --name ip6-b --network ip6-lab busybox:1.36 sleep 300
3. Inspect the assigned IPv6 address and route table.
   COMMAND: docker inspect ip6-a --format '{{range .NetworkSettings.Networks}}{{.GlobalIPv6Address}}{{end}}'
   COMMAND: docker exec ip6-a ip -6 route
4. Prove IPv6 reachability between the containers.
   COMMAND: docker exec ip6-a ping -6 -c1 ip6-b

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove IPv6 lab resources: docker rm -f ip6-a ip6-b 2>/dev/null || true; docker network rm ip6-lab 2>/dev/null || true

## Concept Check
- Which output proves the container joined a real IPv6 subnet instead of only using IPv4?
- What additional failure mode appears when the daemon or host lacks correct IPv6 forwarding or routing?
- Why is dual-stack troubleshooting different from assuming IPv4 and IPv6 behave identically?

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
