# Storage Drivers Overlay Lab

## Goal
Develop hands-on confidence for Storage Drivers Overlay and prove understanding through observable output.

## Prerequisites
- Docker Engine with overlay-based storage driver support.
- Permission to inspect Docker daemon metadata.
- Permission to run commands for this module.

## Steps
1. Inspect the daemon storage driver.
   COMMAND: docker info --format "{{.Driver}}"
2. Start a disposable container and capture its graph-driver data.
   COMMAND: docker run -d --name overlay-lab alpine:3.20 sleep 300
   COMMAND: docker inspect overlay-lab --format "{{json .GraphDriver.Data}}"
3. Write data into the container writable layer.
   COMMAND: docker exec overlay-lab sh -c "echo overlay >/root/proof.txt && ls -l /root/proof.txt"
4. Explain which path is the upper layer and why image layers stayed unchanged.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the overlay test container: docker rm -f overlay-lab 2>/dev/null || true

## Concept Check
- Which inspect field reveals the writable `UpperDir` used for copy-on-write changes?
- Why can troubleshooting writable-layer growth be misleading if you only look at image size?
- What failure mode appears when operators confuse overlay writable data with durable application state?

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
