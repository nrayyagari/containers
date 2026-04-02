# Networking Basics

## Context & Problem
This topic explains how Docker connects containers using bridge, host, none, and user-defined networks. In production, this matters because object-lifecycle mistakes quickly turn into accidental data loss, stale state, or misleading triage.

## First Principles
- Container networking is still Linux networking: interfaces, routes, sockets, bridges, NAT, and packet filters.
- Name resolution, traffic forwarding, and policy enforcement are different hops in the path and can fail independently.
- You do not really understand a network issue until you can describe where the packet should go next.

## Production Implementation
Map the command you run to the object it mutates: image, container, volume, network, or daemon state. Safe Docker operation comes from understanding which state is replaceable and which state must be preserved.

## Troubleshooting Approach
Start by proving where the path breaks: name resolution, route selection, listener binding, translation, or policy. Packet capture or explicit socket inspection is often the fastest way to stop guessing.

## Evolution & Alternatives
Docker's user experience made containers mainstream, but many production stacks now split build, runtime, and orchestration concerns across separate tools. Learning Docker remains useful because it provides the cleanest introduction to the object model.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `docker network create net-lab`
- `docker run -d --name net-a --network net-lab alpine:3.20 sleep 300`
- `docker run -d --name net-b --network net-lab alpine:3.20 sleep 300`
- `docker exec net-a ping -c1 net-b`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- Which result proves service-name resolution on user-defined networks?
- What exposure risk appears when default network behavior is assumed safe?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Dockerfile](../06-dockerfile/README.md).
