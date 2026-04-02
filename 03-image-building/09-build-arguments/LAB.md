# Build Arguments Lab

## Goal
Practice and verify the core behavior of Build Arguments.

## Prerequisites
- Docker installed
- Write access to `/tmp`

## Steps
1. Create build context in `/tmp/img-lab` with `app.sh` and `Dockerfile`.
2. Build image: `docker build -t img-lab:latest /tmp/img-lab`
3. Run image: `docker run --rm img-lab:latest`
4. Inspect layer history: `docker history img-lab:latest`
5. Explain one improvement for cache, size, or security.

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
