# Image Format

## What It Is
Image Format covers How OCI image compatibility affects migration success.

## Why It Matters
It matters because Kubernetes migration fails when Docker assumptions are copied over unchanged.

## Key Points
- Every build step leaves filesystem or metadata history behind.
- Instruction order affects size, cache reuse, and traceability.
- Treat the image as a supply-chain artifact, not as a zip file with a tag.

## Lab Focus
Use the lab to prove how OCI image compatibility affects migration success.
- Key commands:
  - `docker pull nginx:1.27-alpine`
  - `docker image inspect nginx:1.27-alpine --format '{{.Id}} {{index .RepoDigests 0}}'`
  - `skopeo inspect docker://docker.io/library/nginx:1.27-alpine 2>/dev/null | head -n 30 || true`
- Finish only when:
  - Digest captured successfully.
  - You can explain one rollout risk reduced by digest pinning.

## Common Mistakes
- Trusting the tag without checking the actual artifact or digest.
- Blaming runtime behavior that was baked into the image earlier.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Pod Concept](../04-pod-concept/README.md).
