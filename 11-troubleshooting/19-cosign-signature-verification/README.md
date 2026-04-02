# Cosign Signature Verification

## Context & Problem
This topic explains how to verify signatures before trusting an image. In production, this matters because fast recovery depends on collecting the right evidence before changing the system.

## First Principles
- Security controls are layered; no single flag makes a workload safe.
- Least privilege means reducing both what the process is allowed to do and how much trust you place in the artifact it runs from.
- A control is only useful if you can explain what it blocks and how you will verify that block during troubleshooting.

## Production Implementation
Use this topic to build an evidence hierarchy. Start with the least disruptive observation that can narrow the problem and only move to invasive tools once the current evidence no longer explains the symptom.

## Troubleshooting Approach
If the workload fails after hardening, identify the blocking layer before loosening everything. Security debugging is safe only when you can say whether identity, policy, syscall filtering, or trust verification caused the failure.

## Evolution & Alternatives
Troubleshooting used to be dominated by host access and manual inspection. Modern platforms added more layers, which is why disciplined evidence collection is even more important today.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Record the current privilege or trust boundary before making a change so you know what actually improved or broke.
- Use inspection tools such as `docker inspect`, `capsh --print`, `getenforce`, or scanner output as evidence rather than assumptions.
- When you tighten a control, force yourself to explain what new action is now blocked and how you would verify it.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Garbage Collection Cleanup](../20-garbage-collection-cleanup/README.md).
