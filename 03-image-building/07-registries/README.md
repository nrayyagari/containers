# Registries

## What It Is
Registries covers How builds and runtimes interact with image registries.

## Why It Matters
It matters because the image becomes the artifact every runtime and rollback depends on.

## Key Points
- A registry is where builders publish and runtimes fetch immutable artifacts.
- The tag is a pointer; the digest identifies the artifact.
- Reliable delivery depends on the registry path being stable and understandable.

## Lab Focus
Use the lab to prove how builds and runtimes interact with image registries.
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
Then continue to [Tags](../08-tags/README.md).
