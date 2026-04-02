# Best Practices

## What It Is
Best Practices covers How to build images that are small, reproducible, and maintainable.

## Why It Matters
It matters because the image becomes the artifact every runtime and rollback depends on.

## Key Points
- Good image practices make builds smaller, clearer, and easier to trust.
- A best practice is useful only if it improves reproducibility, security, or operability.
- If the image cannot be explained quickly, it will be hard to support later.

## Lab Focus
Use the lab to prove how to build images that are small, reproducible, and maintainable.
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
Then continue to [Registries](../07-registries/README.md).
