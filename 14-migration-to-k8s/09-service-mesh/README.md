# Service Mesh

## What It Is
Service Mesh covers What a service mesh adds and what complexity it introduces.

## Why It Matters
It matters because Kubernetes migration fails when Docker assumptions are copied over unchanged.

## Key Points
- Container networking is still interfaces, routes, sockets, NAT, and DNS underneath.
- Name resolution, forwarding, and policy are separate hops in the path.
- A network issue is not understood until you can describe where the next packet should go.

## Lab Focus
Use the lab to prove what a service mesh adds and what complexity it introduces.
- Finish only when:
  - Benefit and cost are both documented with concrete evidence.
  - You defined one criterion for adopting mesh and one for deferring it.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Monitoring and Observability](../10-monitoring-observability/README.md).
