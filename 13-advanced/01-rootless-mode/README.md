# Rootless Mode

## Context & Problem
This topic explains how rootless execution changes privilege, storage, and networking behavior. In production, this matters because advanced features usually solve a real boundary problem while introducing new operational cost.

## First Principles
- Security controls are layered; no single flag makes a workload safe.
- Least privilege means reducing both what the process is allowed to do and how much trust you place in the artifact it runs from.
- A control is only useful if you can explain what it blocks and how you will verify that block during troubleshooting.

## Production Implementation
Adopt the advanced feature only after you can state the requirement it solves and the host assumptions it introduces. Advanced settings pay for themselves only when the default path is measurably inadequate.

## Troubleshooting Approach
If the workload fails after hardening, identify the blocking layer before loosening everything. Security debugging is safe only when you can say whether identity, policy, syscall filtering, or trust verification caused the failure.

## Evolution & Alternatives
These topics reflect the industry's attempt to get better isolation, better portability, or better density without giving up too much convenience. Every option improves one boundary by making another boundary more complex.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Record the current privilege or trust boundary before making a change so you know what actually improved or broke.
- Use inspection tools such as `docker inspect`, `capsh --print`, `getenforce`, or scanner output as evidence rather than assumptions.
- When you tighten a control, force yourself to explain what new action is now blocked and how you would verify it.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [User Namespaces](../02-user-namespaces/README.md).
