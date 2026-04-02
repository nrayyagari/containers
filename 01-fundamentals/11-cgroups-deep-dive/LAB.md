# Cgroups Deep Dive Lab

## Goal
Practice and verify the core behavior of Cgroups Deep Dive.

## Prerequisites
- Linux host with Docker
- Permission to run containers

## Steps
1. Start a reference container: `docker run -d --name fnd-lab alpine:3.20 sleep 300`
2. Compare host/container process view: `ps -ef | head` and `docker exec fnd-lab ps -ef`
3. Inspect namespace/cgroup hints: `docker inspect fnd-lab --format "{{.State.Pid}}"`
4. Inspect process status inside container: `docker exec fnd-lab cat /proc/1/status | sed -n "1,30p"`
5. Write down what is isolated and what is shared.

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
