# Image Format Lab

## Goal
Prove why digest-based references are safer than tag-only references for migration.

## Prerequisites
- Docker installed.
- Optional: skopeo installed.

## Steps
1. Pull a known image.
   COMMAND: docker pull nginx:1.27-alpine
2. Capture local digest reference.
   COMMAND: docker image inspect nginx:1.27-alpine --format '{{.Id}} {{index .RepoDigests 0}}'
3. Record digest string in notes.
4. Optional manifest inspection.
   COMMAND: skopeo inspect docker://docker.io/library/nginx:1.27-alpine 2>/dev/null | head -n 30 || true

## Expected Observations
- Repo digest is visible and immutable.
- You can contrast mutable tag behavior vs immutable digest behavior.
- Manifest metadata is inspectable through tooling.

## Verify
- Digest captured successfully.
- You can explain one rollout risk reduced by digest pinning.
- You documented one CI gate check for image promotion.

## Cleanup
- COMMAND: docker rmi nginx:1.27-alpine 2>/dev/null || true

## Concept Check
- Which digest/manifest evidence proves artifact immutability for rollout safety?
- What outage class is reduced by digest pinning during migration?
- Which promotion gate should fail when digest evidence is missing?

## Why This Lab Proves Understanding
- You tied artifact identity directly to rollout safety.

## Answer Key
Pass when all Verify points are satisfied and cleanup is complete.
