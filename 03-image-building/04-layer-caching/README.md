# Layer Caching

## What It Is
Layer Caching covers How cache hits and misses affect build speed and reproducibility.

## Why It Matters
It matters because the image becomes the artifact every runtime and rollback depends on.

## Key Points
- Image layers, writable layers, and persistent volumes have different lifecycles.
- Copy-on-write behavior affects both performance and troubleshooting.
- Durability depends on where data is stored, not on whether the write succeeded once.

## Lab Focus
Use the lab to prove how cache hits and misses affect build speed and reproducibility.
- Key commands:
  - `docker build -t img-lab:latest /tmp/img-lab`
  - `docker run --rm img-lab:latest`
  - `docker history img-lab:latest`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Base Images](../05-base-images/README.md).
