# Compose YAML

## What It Is
Compose YAML covers How Compose YAML expresses services, networks, and volumes.

## Why It Matters
It matters because most day-to-day Docker mistakes are object-lifecycle mistakes.

## Key Points
- Compose YAML defines services, networks, volumes, and runtime options declaratively.
- The file describes application topology, not only container flags.
- Good Compose files make dependencies explicit and reduce environment drift.

## Lab Focus
Use the lab to prove how Compose YAML expresses services, networks, and volumes.
- Key commands:
  - `docker network create net-lab`
  - `docker run -d --name net-a --network net-lab alpine:3.20 sleep 300`
  - `docker run -d --name net-b --network net-lab alpine:3.20 sleep 300`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Image Building](../../03-image-building/README.md).
