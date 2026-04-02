# Storage Migration

## Context & Problem
Ephemeral container layers cause data loss when workloads move/restart unless durable storage is explicit.

## First Principles
PVC/PV abstractions provide durable lifecycle decoupled from individual pods.

## Production Implementation
Classify stateful workloads and map to storage class + backup/restore SLOs.

## Troubleshooting Approach
For data loss, verify bind state, mount path, and reclaim behavior.

## Next Steps
Use this lab to prove persistence across pod recreation.

## Hands-on Lab
Use [LAB.md](./LAB.md) to practice and verify this concept.

## Zero-Confusion Summary
- What it is:
  - Storage Migration as a Kubernetes migration control area.
- What it is not:
  - It is not a standalone migration strategy.
- When to use:
  - Use it when this layer becomes a migration blocker or risk.
- If you truly understand this topic, you can explain:
  - The problem it solves.
  - The mechanism involved.
  - One failure mode and fix path.
