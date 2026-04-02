# Image Format Lab

## Goal
Inspect image metadata and practice digest-based deployment references.

## Prerequisites
- Docker installed
- `skopeo` (optional, useful)

## Steps
1. Pull a known image:
   ```bash
   docker pull nginx:1.27-alpine
   ```
2. Inspect image ID and digest locally:
   ```bash
   docker image inspect nginx:1.27-alpine --format '{{.Id}} {{index .RepoDigests 0}}'
   ```
3. Save a digest-pinned reference from output.
4. (Optional) Inspect manifest/media type with skopeo:
   ```bash
   skopeo inspect docker://docker.io/library/nginx:1.27-alpine | head -n 30
   ```
5. Compare operational meaning:
   - Tag reference: mutable over time
   - Digest reference: immutable content pointer

## Verify
- You captured and can explain a valid repo digest for the image.
- You can state why digest pinning improves reproducibility.
- Optional `skopeo inspect` confirms manifest metadata visibility.

## Cleanup
- `docker rmi nginx:1.27-alpine || true`

## Next
Enforce digest pinning in deployment manifests and policy checks.

## Concept Check
- Why is a digest a stronger deployment contract than a tag?
- What real outage class is reduced by digest pinning?
- Which check should CI enforce before allowing an image promotion?

## Why This Lab Proves Understanding
- Verify confirms you can inspect image identity and reason about immutability.
- Cleanup confirms environment reset discipline.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] You captured and can explain a valid repo digest for the image.
- [ ] You can state why digest pinning improves reproducibility.
- [ ] Optional `skopeo inspect` confirms manifest metadata visibility (if tool installed).
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any mandatory Verify condition not met.
- Digest understanding is unclear or incorrect.
- Environment not in clean state after cleanup.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
