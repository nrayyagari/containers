# Image Signing Lab

## Goal
Develop hands-on confidence for Image Signing and prove understanding through observable output.

## Prerequisites
- Cosign installed and internet access available.
- Access to an OCI registry you can push to; this lab uses `ttl.sh` as a short-lived public test registry.
- Permission to run commands for this module.

## Steps
1. Create a short-lived registry reference and copy a test image there.
   COMMAND: IMAGE_NAME=$(uuidgen | tr "[:upper:]" "[:lower:]")
   COMMAND: export IMAGE=ttl.sh/${IMAGE_NAME}:1h
   COMMAND: cosign copy alpine:3.20 ${IMAGE}
2. Generate a lab-only key pair.
   COMMAND: rm -f cosign.key cosign.pub
   COMMAND: COSIGN_PASSWORD="" cosign generate-key-pair
3. Sign the image and then verify the signature with the public key.
   COMMAND: COSIGN_PASSWORD="" cosign sign --key cosign.key ${IMAGE}
   COMMAND: cosign verify --key cosign.pub ${IMAGE}
4. Inspect the verified payload and record the manifest digest that was signed.
   COMMAND: cosign verify --key cosign.pub ${IMAGE} | jq -r '.[0].critical.image["docker-manifest-digest"]'

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the control, privilege boundary, or verification result.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove signing keys after the lab: rm -f cosign.key cosign.pub

## Concept Check
- Which output proves the signature is bound to an immutable image digest rather than just the tag string?
- Why is signing useful for origin and integrity but insufficient as a replacement for runtime hardening?
- What key-management decision becomes the next most important control once signing is in place?

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
