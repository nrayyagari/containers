# Network Namespaces Lab

## Goal
Develop hands-on confidence for Network Namespaces and prove understanding through observable output.

## Prerequisites
- Linux host with Docker Engine and `nsenter` available.
- Permission to inspect container PIDs from the host.
- Permission to run commands for this module.

## Steps
1. Start a disposable container.
   COMMAND: docker run -d --name netns-lab alpine:3.20 sleep 300
2. Capture the container PID from Docker.
   COMMAND: PID=$(docker inspect --format '{{.State.Pid}}' netns-lab); echo "$PID"
3. Enter the container network namespace and inspect interfaces and routes.
   COMMAND: nsenter -t "$PID" -n ip addr
   COMMAND: nsenter -t "$PID" -n ip route
4. Compare the host network namespace to the container namespace.
   COMMAND: ip addr

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the path, boundary, or translation.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the namespace lab container: docker rm -f netns-lab 2>/dev/null || true

## Concept Check
- Which interface or route proves you are no longer looking at the host namespace?
- Why does the container still need a veth pair even though it appears to own `eth0` internally?
- What diagnostic advantage does `nsenter` give you over guessing from application logs?

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
