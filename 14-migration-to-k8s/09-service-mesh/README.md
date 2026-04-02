# Service Mesh

## Context & Problem
This topic explains what a service mesh adds and what complexity it introduces. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.
A service mesh is not just another load balancer. It introduces a programmable data plane into service-to-service traffic.

## First Principles
- Container networking is still Linux networking: interfaces, routes, sockets, bridges, NAT, and packet filters.
- Name resolution, traffic forwarding, and policy enforcement are different hops in the path and can fail independently.
- You do not really understand a network issue until you can describe where the packet should go next.

## Production Implementation
Use this topic to challenge a Docker-era assumption directly. In migration work, the risk is not ignorance of YAML; it is keeping the old mental model after the platform boundary has changed.

## Troubleshooting Approach
Start by proving where the path breaks: name resolution, route selection, listener binding, translation, or policy. Packet capture or explicit socket inspection is often the fastest way to stop guessing.

## Evolution & Alternatives
Service meshes emerged when teams wanted stronger traffic policy, mutual TLS, retries, and observability without pushing that logic into every application. The trade-off is extra data-plane complexity and a new failure domain.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- Read the lab and identify the commands that expose the mechanism directly.

### What Success Looks Like
- Benefit and cost are both documented with concrete evidence.
- You defined one criterion for adopting mesh and one for deferring it.
- You mapped one failure mode to mesh-vs-app diagnostic path.

### Questions To Answer After The Lab
- Which specific control became easier with mesh in your tested flow?
- What operational overhead did you observe that must be budgeted?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Monitoring and Observability](../10-monitoring-observability/README.md).
