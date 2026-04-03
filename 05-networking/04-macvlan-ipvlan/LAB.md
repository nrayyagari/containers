# Macvlan and Ipvlan Lab

## Goal
Develop hands-on confidence for Macvlan and Ipvlan and prove understanding through observable output.

## Prerequisites
- Linux host with root privileges and support for creating dummy interfaces.
- Do not run this on Docker Desktop or on a shared production host.
- Permission to run commands for this module.

## Steps
1. Create a disposable parent interface for the lab.
   COMMAND: ip link add mv-parent type dummy || true
   COMMAND: ip addr add 192.168.250.1/24 dev mv-parent || true
   COMMAND: ip link set mv-parent up
2. Create a macvlan network that uses the dummy parent.
   COMMAND: docker network create -d macvlan --subnet 192.168.250.0/24 --gateway 192.168.250.1 -o parent=mv-parent mv-lab
3. Run a container with a directly assigned IP on that network.
   COMMAND: docker run -d --name mv-a --network mv-lab --ip 192.168.250.10 alpine:3.20 sleep 300
4. Inspect the container IP and MAC, then explain how an ipvlan design would differ.
   COMMAND: docker inspect mv-a --format '{{range .NetworkSettings.Networks}}{{.IPAddress}} {{.MacAddress}}{{end}}'
   COMMAND: docker network inspect mv-lab

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove lab resources: docker rm -f mv-a 2>/dev/null || true; docker network rm mv-lab 2>/dev/null || true; ip link del mv-parent 2>/dev/null || true

## Concept Check
- Which output proves the container received its own layer-2 identity?
- Why can host-to-container communication still surprise people on macvlan and ipvlan designs?
- When would ipvlan be preferable to macvlan on a constrained physical network?

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
