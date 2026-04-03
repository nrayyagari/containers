# Docker Hub Lab

## Goal
Develop hands-on confidence for Docker Hub and prove understanding through observable output.

## Prerequisites
- Docker CLI with internet access to pull public images.
- `jq` available if you want to inspect manifest JSON more comfortably.
- Permission to run commands for this module.

## Steps
1. Pull a public image from Docker Hub by tag.
   COMMAND: docker pull alpine:3.20
2. Record the immutable digest associated with the pulled image.
   COMMAND: docker image inspect alpine:3.20 --format "{{index .RepoDigests 0}}"
3. Inspect the remote manifest metadata for the tag.
   COMMAND: docker manifest inspect alpine:3.20 | jq ".schemaVersion, .mediaType"
4. Pull the same image again by digest and compare it to the tag-based reference.
   COMMAND: DIGEST=$(docker image inspect alpine:3.20 --format "{{index .RepoDigests 0}}" | cut -d@ -f2)
   COMMAND: docker pull alpine@${DIGEST}

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- No persistent cleanup is required for this lab.

## Concept Check
- Which output proves the tag is only a pointer while the digest is the true immutable identity?
- What operational risk appears if deployments pin only tags during high-change periods or under rate limits?
- Why is digest-based pull verification more trustworthy than assuming a familiar public tag still points to the same content?

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
