# Volume Drivers Lab

## Goal
Develop hands-on confidence for Volume Drivers and prove understanding through observable output.

## Prerequisites
- Docker Engine with local volume driver support.
- Host path `/tmp/driver-lab` available for disposable backend storage.
- Permission to run commands for this module.

## Steps
1. Prepare a backend path on the host.
   COMMAND: mkdir -p /tmp/driver-lab
2. Inspect installed Docker plugins and drivers.
   COMMAND: docker plugin ls || true
3. Create a volume with local-driver options that bind it to the backend path.
   COMMAND: docker volume create --driver local --opt type=none --opt device=/tmp/driver-lab --opt o=bind driver-lab
4. Mount the volume, write a file, and prove the backend path received it.
   COMMAND: docker run --rm -v driver-lab:/data alpine:3.20 sh -c "echo driver-proof >/data/proof.txt"
   COMMAND: ls -l /tmp/driver-lab/proof.txt
   COMMAND: docker volume inspect driver-lab

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves where the data lives or why it persists.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove driver lab resources: docker volume rm driver-lab 2>/dev/null || true; rm -rf /tmp/driver-lab

## Concept Check
- Which output proves the volume driver is translating Docker intent into a specific backend path or plugin?
- What operational risk appears when the declared driver does not match the durability guarantees you expect?
- Why should you inspect the effective backend before trusting a plugin-based storage design?

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
