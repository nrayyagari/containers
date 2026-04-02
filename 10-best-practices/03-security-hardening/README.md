# Security Hardening

## Context & Problem
This topic explains how to reduce privileges, patch exposure, and supply-chain risk. In production, this matters because small shortcuts here create recurring reliability, security, and rollout problems later.

## First Principles
- Security controls are layered; no single flag makes a workload safe.
- Least privilege means reducing both what the process is allowed to do and how much trust you place in the artifact it runs from.
- A control is only useful if you can explain what it blocks and how you will verify that block during troubleshooting.

## Production Implementation
The point of a best practice is to reduce ambiguity, blast radius, or recovery cost. Apply the pattern only if you can name which of those it improves for your workload.

## Troubleshooting Approach
If the workload fails after hardening, identify the blocking layer before loosening everything. Security debugging is safe only when you can say whether identity, policy, syscall filtering, or trust verification caused the failure.

## Evolution & Alternatives
Best practices keep changing in detail as tooling improves, but they almost always move in the same direction: fewer surprises, less privilege, stronger provenance, and faster recovery.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Record the current privilege or trust boundary before making a change so you know what actually improved or broke.
- Use inspection tools such as `docker inspect`, `capsh --print`, `getenforce`, or scanner output as evidence rather than assumptions.
- When you tighten a control, force yourself to explain what new action is now blocked and how you would verify it.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Multi Stage Builds](../04-multi-stage-builds/README.md).
