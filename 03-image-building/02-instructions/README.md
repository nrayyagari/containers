# Instructions

## What It Is
Instructions covers What common Dockerfile instructions do at build time and run time.

## Why It Matters
It matters because the image becomes the artifact every runtime and rollback depends on.

## Key Points
- Each Dockerfile instruction changes either filesystem state, metadata, or both.
- Some instructions affect only build-time behavior, while others shape runtime defaults.
- Instruction order changes cache behavior and final image history.

## Lab Focus
Use the lab to prove what common Dockerfile instructions do at build time and run time.
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
Then continue to [Multi Stage Builds](../03-multi-stage-builds/README.md).
