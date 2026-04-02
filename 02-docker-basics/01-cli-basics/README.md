# Cli Basics

## What It Is
Cli Basics covers How Docker CLI commands map to object lifecycle operations.

## Why It Matters
It matters because most day-to-day Docker mistakes are object-lifecycle mistakes.

## Key Points
- Docker CLI commands either create, inspect, change, or delete an object.
- Confusion starts when images, containers, volumes, and networks are treated as one thing.
- Safe CLI use starts with inspection before mutation or cleanup.

## Lab Focus
Use the lab to prove how Docker CLI commands map to object lifecycle operations.
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
Then continue to [Images](../02-images/README.md).
