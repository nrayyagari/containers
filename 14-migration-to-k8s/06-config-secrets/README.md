# Config and Secrets

## Context & Problem
Baking config/secrets into images increases leakage risk and slows operational changes.

## First Principles
ConfigMap and Secret serve distinct security/operational purposes.

## Production Implementation
Inject config/secrets at runtime and plan rotation without image rebuild.

## Troubleshooting Approach
For auth/config failures, inspect mounts/env values and secret versions.

## Next Steps
Run this lab to enforce separation and rotation readiness.

## Hands-on Lab
Use [LAB.md](./LAB.md) to practice and verify this concept.

## Zero-Confusion Summary
- What it is:
  - Config and Secrets as a Kubernetes migration control area.
- What it is not:
  - It is not a standalone migration strategy.
- When to use:
  - Use it when this layer becomes a migration blocker or risk.
- If you truly understand this topic, you can explain:
  - The problem it solves.
  - The mechanism involved.
  - One failure mode and fix path.
