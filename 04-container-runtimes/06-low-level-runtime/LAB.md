# Low Level Runtime Lab

## Goal
Practice and verify the core behavior of Low Level Runtime.

## Prerequisites
- Linux host with Docker/container runtime
- Optional: `crictl` installed

## Steps
1. Check runtime service/processes: `systemctl status containerd --no-pager || true` and `ps -ef | grep -E "containerd|shim|runc"`
2. Run reference container: `docker run -d --name rt-lab alpine:3.20 sleep 300`
3. Inspect PID/runtime metadata: `docker inspect rt-lab --format "{{.State.Pid}}"`
4. Optional CRI view: `crictl ps -a || true`
5. Map observed evidence to runtime layers (manager, shim, low-level runtime).

## Verify
- The lab commands execute successfully for this topic.
- You can explain one concrete behavior observed in output.
- You can describe one production risk if this concept is misused.

## Cleanup
- Remove lab container/images/resources created in this lab.
- Confirm no leftover temporary resources remain.

## Concept Check
- Which command output in this lab is your strongest proof of understanding?
- Which failure mode appears when this concept is misunderstood?
- What should be the first diagnostic check in a real incident?

## Why This Lab Proves Understanding
- Verify checks observable behavior, not only command memorization.
- Cleanup confirms operational discipline and repeatability.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] The lab commands execute successfully for this topic.
- [ ] You can explain one concrete behavior observed in output.
- [ ] You can describe one production risk if this concept is misused.
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Output differs materially from expected behavior.
- Environment not in clean state after cleanup.
