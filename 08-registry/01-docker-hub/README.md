# Docker Hub

## What It Is
Docker Hub covers How the default public registry works and what its limits are.

## Why It Matters
It matters because every pull and push is part of the software supply chain.

## Key Points
- Docker Hub is convenient because it is widely used and easy to reach.
- Public registries add external dependency, rate-limit, and provenance concerns.
- Teams should know when convenience stops being enough for production needs.

## Practice Check
- Inspect one image by tag and by digest so the difference becomes concrete.
- Use `skopeo inspect`, `curl /v2/`, or a registry UI to verify what object really exists.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Private Registry](../02-private-registry/README.md).
