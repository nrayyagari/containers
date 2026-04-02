# Orchestration Basics

## Context & Problem
Manual container management breaks once workloads move between hosts and replica counts change under load. Orchestration exists because location, health, scaling, and configuration stop being human-manageable very quickly.

## First Principles
An orchestrator is a control system. You declare desired state, the platform observes actual state, and controllers keep reconciling the difference. That means service discovery, load balancing, scheduling, and rollback are all parts of one operating model.

## Production Implementation
Think in terms of control loops and workload identity rather than host identity. Reliable operations come from describing the desired outcome clearly and letting the platform keep converging toward it.

## Troubleshooting Approach
When the platform does something unexpected, ask which controller is responsible, what state it believes is true, and what signal it is reacting to. That is usually more useful than staring at one container in isolation.

## Evolution & Alternatives
Orchestration grew from process supervisors and cluster schedulers into full declarative control planes. Kubernetes is the dominant example today, but the mental model applies more broadly than one product.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-what-is-orchestration](./01-what-is-orchestration/README.md): why schedulers exist once containers outgrow manual host-by-host management.
- [02-service-discovery](./02-service-discovery/README.md): how clients find the right backend instance as workloads move.
- [03-load-balancing](./03-load-balancing/README.md): how traffic is distributed across healthy replicas.
- [04-scaling](./04-scaling/README.md): how systems add or remove replicas in response to demand or policy.
- [05-health-checks](./05-health-checks/README.md): how platforms distinguish a started container from a usable service.
- [06-self-healing](./06-self-healing/README.md): how orchestration loops replace failed tasks and converge back to desired state.
- [07-rollout-rollback](./07-rollout-rollback/README.md): how new versions are introduced and reversed without full outages.
- [08-config-management](./08-config-management/README.md): how runtime configuration is injected without rebuilding images.
- [09-scheduling](./09-scheduling/README.md): how the platform decides where a workload should run.
- [10-reconciliation](./10-reconciliation/README.md): why declarative systems continuously correct drift.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After this module, the Best Practices and Migration to Kubernetes sections will feel much more concrete because you will understand how desired state gets enforced.
Continue with [Best Practices](../10-best-practices/README.md) when the topic map in this module feels operationally clear.
