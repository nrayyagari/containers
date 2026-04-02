# Build Secrets

## What It Is
Build Secrets covers How BuildKit passes sensitive material without baking it into layers.

## Why It Matters
It matters because the image becomes the artifact every runtime and rollback depends on.

## Key Points
- Container security is layered; no single flag makes a workload safe.
- Least privilege means reducing what the process can do and what you trust it with.
- A security control is only useful if you can explain what it blocks.

## Lab Focus
Use the lab to prove how BuildKit passes sensitive material without baking it into layers.
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
Then continue to [Container Runtimes](../../04-container-runtimes/README.md).
