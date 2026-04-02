# Scheduling

## Context & Problem
This topic explains how the platform decides where a workload should run. In production, this matters because once workloads become scheduled and replicated, host-centric mental models stop working.

## First Principles
- Orchestration is a control-loop problem, not a one-host execution problem.
- Desired state, observed state, and controller actions must stay aligned for the system to feel reliable.
- Once replicas move between nodes, service identity matters more than host identity.

## Production Implementation
Think in controller terms, not in single-container terms. What matters is which object owns the desired state, which signal it reacts to, and how a change propagates across replicas.

## Troubleshooting Approach
Ask which controller owns the behavior you are observing and what signal it reacted to. Problems that look random from one Pod often look obvious from the controller's point of view.

## Evolution & Alternatives
The shift from imperative operations to declarative reconciliation changed how teams think about reliability. You no longer keep one process alive by hand; you define the desired state and let controllers keep returning to it.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Pick one workload and describe its desired state, the controller that owns it, and the signals that controller reacts to.
- Practice predicting what should happen during a scale event, health failure, or rollout before looking at the platform output.
- Validate the prediction by checking object state and then explaining which control loop caused it.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Reconciliation](../10-reconciliation/README.md).
