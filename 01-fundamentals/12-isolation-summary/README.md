# Isolation Summary

## What It Is
Isolation Summary covers How these primitives combine into a container boundary.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- Container isolation is the combination of visibility, resource control, filesystem view, and privilege limits.
- Weakness in any one layer can make the whole boundary less trustworthy.
- Summarizing the model matters because real incidents usually cross more than one layer.

## Lab Focus
Use the lab to prove how these primitives combine into a container boundary.
- Key commands:
  - `docker run -d --name fnd-lab alpine:3.20 sleep 300`
  - `docker inspect fnd-lab --format "{{.State.Pid}} {{.State.Status}}"`
  - `docker exec fnd-lab cat /proc/1/status | sed -n '1,25p'`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Docker Basics](../../02-docker-basics/README.md).
