# Containers

## What It Is
Containers covers How containers move through create, start, stop, and remove.

## Why It Matters
It matters because most day-to-day Docker mistakes are object-lifecycle mistakes.

## Key Points
- A container is runtime state built from an image plus configuration.
- Container lifecycle and image lifecycle are related but separate.
- Restart, stop, remove, and recreate are not equivalent actions.

## Lab Focus
Use the lab to prove how containers move through create, start, stop, and remove.
- Key commands:
  - `docker pull alpine:3.20`
  - `docker run -d --name dk-lab alpine:3.20 sleep 300`
  - `docker inspect dk-lab --format "{{.Config.Image}} {{.State.Status}}"`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Volumes](../04-volumes/README.md).
