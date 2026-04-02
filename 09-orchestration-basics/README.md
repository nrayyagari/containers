# Orchestration Basics

## What This Module Covers
This module explains why schedulers exist and how desired state, health, scaling, rollout, service discovery, and reconciliation fit together. It is the bridge from single-host container thinking to platform thinking.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-what-is-orchestration](./01-what-is-orchestration/README.md): why schedulers exist once containers outgrow manual host-by-host management.
- [02-service-discovery](./02-service-discovery/README.md): how clients find the right backend instance as workloads move.
- [03-load-balancing](./03-load-balancing/README.md): how traffic is distributed across healthy replicas.
- [04-scaling](./04-scaling/README.md): how systems add or remove replicas in response to demand or policy.
- [05-health-checks](./05-health-checks/README.md): how platforms distinguish a started container from a usable service.
- [06-self-healing](./06-self-healing/README.md): how control loops replace failed tasks and converge back to desired state.
- [07-rollout-rollback](./07-rollout-rollback/README.md): how new versions are introduced and reversed safely.
- [08-config-management](./08-config-management/README.md): how runtime configuration is injected without rebuilding images.
- [09-scheduling](./09-scheduling/README.md): how the platform decides where a workload should run.
- [10-reconciliation](./10-reconciliation/README.md): why declarative systems continuously correct drift.

## Move On When
- You can meet this module's main goal: Think in controllers and desired state, not in one host and one process.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Best Practices](../10-best-practices/README.md).
