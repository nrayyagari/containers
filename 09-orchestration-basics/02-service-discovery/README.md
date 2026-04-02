# Service Discovery

## Context & Problem
This topic explains how clients find the right backend instance as workloads move. In production, this matters because once workloads become scheduled and replicated, host-centric mental models stop working.

## First Principles
- Container networking is still Linux networking: interfaces, routes, sockets, bridges, NAT, and packet filters.
- Name resolution, traffic forwarding, and policy enforcement are different hops in the path and can fail independently.
- You do not really understand a network issue until you can describe where the packet should go next.

## Production Implementation
Think in controller terms, not in single-container terms. What matters is which object owns the desired state, which signal it reacts to, and how a change propagates across replicas.

## Troubleshooting Approach
Start by proving where the path breaks: name resolution, route selection, listener binding, translation, or policy. Packet capture or explicit socket inspection is often the fastest way to stop guessing.

## Evolution & Alternatives
The shift from imperative operations to declarative reconciliation changed how teams think about reliability. You no longer keep one process alive by hand; you define the desired state and let controllers keep returning to it.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Pick one workload and describe its desired state, the controller that owns it, and the signals that controller reacts to.
- Practice predicting what should happen during a scale event, health failure, or rollout before looking at the platform output.
- Validate the prediction by checking object state and then explaining which control loop caused it.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Load Balancing](../03-load-balancing/README.md).
