# Networking Changes

## Context & Problem
Docker bridge assumptions do not directly map to Service DNS and NetworkPolicy behavior.

## First Principles
Kubernetes gives pod-IP model, service discovery, and policy-based traffic constraints.

## Production Implementation
Define service boundaries and explicit policy before migration at scale.

## Troubleshooting Approach
Debug path: DNS resolution -> endpoints -> policy allow/deny effects.

## Next Steps
Run connectivity tests before and after policy changes.

## Hands-on Lab
Use [LAB.md](./LAB.md) to practice and verify this concept.

## Zero-Confusion Summary
- What it is:
  - Networking Changes as a Kubernetes migration control area.
- What it is not:
  - It is not a standalone migration strategy.
- When to use:
  - Use it when this layer becomes a migration blocker or risk.
- If you truly understand this topic, you can explain:
  - The problem it solves.
  - The mechanism involved.
  - One failure mode and fix path.
