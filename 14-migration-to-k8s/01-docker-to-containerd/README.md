# Docker to containerd

## Context & Problem
Docker CLI habits often hide the runtime realities Kubernetes uses on nodes.

## First Principles
Kubernetes uses CRI-facing runtimes; containerd is runtime-focused while Docker includes broader developer workflows.

## Production Implementation
Map operational checks to crictl/containerd before migration waves.

## Troubleshooting Approach
When workloads fail, inspect runtime state via crictl before assuming Docker daemon issues.

## Next Steps
Practice runtime-layer diagnosis and command mapping.

## Hands-on Lab
Use [LAB.md](./LAB.md) to practice and verify this concept.

## Zero-Confusion Summary
- What it is:
  - Docker to containerd as a Kubernetes migration control area.
- What it is not:
  - It is not a standalone migration strategy.
- When to use:
  - Use it when this layer becomes a migration blocker or risk.
- If you truly understand this topic, you can explain:
  - The problem it solves.
  - The mechanism involved.
  - One failure mode and fix path.
