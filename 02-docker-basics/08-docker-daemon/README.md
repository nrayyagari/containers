# Docker Daemon

## What It Is
Docker Daemon covers How the Docker daemon brokers build and runtime operations.

## Why It Matters
It matters because most day-to-day Docker mistakes are object-lifecycle mistakes.

## Key Points
- The Docker daemon is the control point for build, image, network, and container operations.
- CLI commands are client requests; the daemon owns the actual state transitions.
- Daemon issues can affect many workloads at once because the control plane is centralized.

## Lab Focus
Use the lab to prove how the Docker daemon brokers build and runtime operations.
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
Then continue to [Storage Driver](../09-storage-driver/README.md).
