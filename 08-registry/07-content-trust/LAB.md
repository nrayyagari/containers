# Content Trust Lab

## Goal
Develop hands-on confidence for Content Trust and prove understanding through observable output.

## Prerequisites
- Cosign installed and internet access available.
- Use a modern OCI signing flow for this lab rather than the legacy `docker trust` workflow.
- Permission to run commands for this module.

## Steps
1. Create a short-lived registry reference and copy a test image there.
   COMMAND: IMAGE_NAME=$(uuidgen | tr "[:upper:]" "[:lower:]")
   COMMAND: export IMAGE=ttl.sh/${IMAGE_NAME}:1h
   COMMAND: cosign copy alpine:3.20 ${IMAGE}
2. Generate a local signing key pair.
   COMMAND: rm -f cosign.key cosign.pub
   COMMAND: COSIGN_PASSWORD="" cosign generate-key-pair
3. Sign the image and verify it before use.
   COMMAND: COSIGN_PASSWORD="" cosign sign --key cosign.key ${IMAGE}
   COMMAND: cosign verify --key cosign.pub ${IMAGE}
4. Extract the verified manifest digest and explain why trust is digest-first, not tag-first.
   COMMAND: cosign verify --key cosign.pub ${IMAGE} | jq -r '.[0].critical.image["docker-manifest-digest"]'

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove content-trust lab keys: rm -f cosign.key cosign.pub

## Concept Check
- Which output proves you verified a signed digest rather than simply trusting a registry tag?
- Why is signature verification complementary to vulnerability scanning instead of a substitute for it?
- What policy decision must happen next if you want trust verification to affect deployment behavior automatically?

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
