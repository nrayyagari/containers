# Networking Changes

## Context & Problem
This topic explains how moving to Kubernetes changes service exposure, DNS, and network policy. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.

## First Principles
- Container networking is still Linux networking: interfaces, routes, sockets, bridges, NAT, and packet filters.
- Name resolution, traffic forwarding, and policy enforcement are different hops in the path and can fail independently.
- You do not really understand a network issue until you can describe where the packet should go next.

## Production Implementation
Use this topic to challenge a Docker-era assumption directly. In migration work, the risk is not ignorance of YAML; it is keeping the old mental model after the platform boundary has changed.

## Troubleshooting Approach
Start by proving where the path breaks: name resolution, route selection, listener binding, translation, or policy. Packet capture or explicit socket inspection is often the fastest way to stop guessing.

## Evolution & Alternatives
Migration thinking changed after dockershim removal and the rise of CRI-native nodes. The successful path now is to adopt Kubernetes-native operating concepts rather than preserve Docker-era habits behind new YAML.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `kubectl create ns net-mig`
- `kubectl -n net-mig create deployment web --image=nginx:1.27-alpine`
- `kubectl -n net-mig expose deployment web --port=80 --name web`
- `kubectl -n net-mig run client --image=alpine:3.20 --restart=Never --command -- sh -c 'sleep 300'`

### What Success Looks Like
- DNS/service access success before deny.
- Access blocked after deny.
- You documented required allow policy shape for restoration.

### Questions To Answer After The Lab
- Which test result proves policy-driven connectivity change (not app failure)?
- What sequencing error in policy rollout can create accidental outage?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Storage Migration](../08-storage-migration/README.md).
