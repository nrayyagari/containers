# Load Balancing

## What It Is
Load Balancing covers How traffic is distributed across healthy replicas.

## Why It Matters
It matters because single-host thinking breaks once replicas move and controllers own state.

## Key Points
- Container networking is still interfaces, routes, sockets, NAT, and DNS underneath.
- Name resolution, forwarding, and policy are separate hops in the path.
- A network issue is not understood until you can describe where the next packet should go.

## Practice Check
- Pick one workload and state the controller, desired state, and health signal.
- Predict what the platform should do during failure or rollout, then verify it.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Scaling](../04-scaling/README.md).
