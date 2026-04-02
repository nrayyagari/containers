# Containers Lab

## Goal
Practice and verify the core behavior of Containers.

## Prerequisites
- Docker installed
- Internet access to pull public images

## Steps
1. Pull image: `docker pull alpine:3.20`
2. Start container: `docker run -d --name dk-lab alpine:3.20 sleep 300`
3. Inspect runtime state: `docker ps --filter name=dk-lab` and `docker inspect dk-lab --format "{{.State.Status}}"`
4. Exec into container: `docker exec dk-lab sh -c "id && hostname"`
5. Record image state vs container runtime state.

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
