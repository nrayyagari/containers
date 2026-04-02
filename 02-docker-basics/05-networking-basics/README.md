# Networking Basics

## What It Is
Networking Basics covers How Docker connects containers with built-in network modes.

## Why It Matters
It matters because most day-to-day Docker mistakes are object-lifecycle mistakes.

## Key Points
- Container networking is still interfaces, routes, sockets, NAT, and DNS underneath.
- Name resolution, forwarding, and policy are separate hops in the path.
- A network issue is not understood until you can describe where the next packet should go.

## Lab Focus
Use the lab to prove how Docker connects containers with built-in network modes.
- Key commands:
  - `docker network create net-lab`
  - `docker run -d --name net-a --network net-lab alpine:3.20 sleep 300`
  - `docker run -d --name net-b --network net-lab alpine:3.20 sleep 300`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Changing app config before proving the packet path.
- Treating DNS, routing, and firewall behavior as one problem.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Dockerfile](../06-dockerfile/README.md).
