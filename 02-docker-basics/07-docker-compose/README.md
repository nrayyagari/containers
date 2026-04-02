# Docker Compose

## What It Is
Docker Compose describes a multi-container application in one file and brings the services up together. It is an application-topology tool, not just a shortcut for several `docker run` commands.

## Why It Matters
It reduces setup drift, but it also hides object creation unless you keep the service, network, and volume model clear.

## Key Points
- Compose describes an application, not just a list of commands.
- Services, networks, and volumes created by Compose have their own lifecycle.
- Startup order is not the same thing as readiness.

## Lab Focus
Use the lab to prove how Compose describes and runs multi-container applications.
- Key commands:
  - `docker network create net-lab`
  - `docker run -d --name net-a --network net-lab alpine:3.20 sleep 300`
  - `docker run -d --name net-b --network net-lab alpine:3.20 sleep 300`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Assuming Compose startup order guarantees readiness.
- Forgetting that Compose also creates networks and volumes with their own lifecycle.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Docker Daemon](../08-docker-daemon/README.md).
