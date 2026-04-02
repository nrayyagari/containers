# Monitoring and Observability

## Context & Problem
Migration incidents remain unresolved when teams only watch host CPU/memory and ignore Kubernetes signals.

## First Principles
Reliable diagnosis needs correlated metrics, logs, traces, events, and rollout state.

## Production Implementation
Define migration SLOs and baseline signals pre-cutover; enforce post-change checks.

## Troubleshooting Approach
Correlate deployment change with pod events, logs, and error/latency signals.

## Next Steps
Run baseline->change->correlate flow and produce reusable checklist.

## Hands-on Lab
Use [LAB.md](./LAB.md) to practice and verify this concept.

## Zero-Confusion Summary
- What it is:
  - Monitoring and Observability as a Kubernetes migration control area.
- What it is not:
  - It is not a standalone migration strategy.
- When to use:
  - Use it when this layer becomes a migration blocker or risk.
- If you truly understand this topic, you can explain:
  - The problem it solves.
  - The mechanism involved.
  - One failure mode and fix path.
