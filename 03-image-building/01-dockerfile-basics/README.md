# Dockerfile Basics

## What It Is
Dockerfile Basics covers How Dockerfile order and defaults shape the final image.

## Why It Matters
It matters because the image becomes the artifact every runtime and rollback depends on.

## Key Points
- Every build step leaves filesystem or metadata history behind.
- Instruction order affects size, cache reuse, and traceability.
- Treat the image as a supply-chain artifact, not as a zip file with a tag.

## Lab Focus
Use the lab to prove how Dockerfile order and defaults shape the final image.
- Key commands:
  - `docker build -t img-lab:latest /tmp/img-lab`
  - `docker run --rm img-lab:latest`
  - `docker history img-lab:latest`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Trusting the tag without checking the actual artifact or digest.
- Blaming runtime behavior that was baked into the image earlier.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Instructions](../02-instructions/README.md).
