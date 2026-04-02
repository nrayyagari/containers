# Config Management

## What It Is
Config Management covers How runtime configuration is injected without rebuilding images.

## Why It Matters
It matters because single-host thinking breaks once replicas move and controllers own state.

## Key Points
- Orchestration is about desired state and control loops.
- Service identity matters more than host identity once workloads move.
- Health, scaling, rollout, and scheduling are connected, not separate concerns.

## Practice Check
- Pick one workload and state the controller, desired state, and health signal.
- Predict what the platform should do during failure or rollout, then verify it.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Scheduling](../09-scheduling/README.md).
