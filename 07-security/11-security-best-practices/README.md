# Security Best Practices

## Context & Problem
This topic explains how to combine build-time, runtime, and registry controls into defense in depth. In production, this matters because container security fails when teams treat one control as sufficient instead of layering identity, policy, and trust.

## First Principles
- Security controls are layered; no single flag makes a workload safe.
- Least privilege means reducing both what the process is allowed to do and how much trust you place in the artifact it runs from.
- A control is only useful if you can explain what it blocks and how you will verify that block during troubleshooting.

## Production Implementation
Treat this control as one layer in a defense-in-depth model. Production hardening means preserving just enough privilege for the workload to function and then proving that the control you added is actually enforced.

## Troubleshooting Approach
If the workload fails after hardening, identify the blocking layer before loosening everything. Security debugging is safe only when you can say whether identity, policy, syscall filtering, or trust verification caused the failure.

## Evolution & Alternatives
Container security shifted from 'don't run everything as root' into a broader supply-chain and runtime-hardening discipline. The deeper improvement was treating trust as an end-to-end property rather than a runtime-only property.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Record the current privilege or trust boundary before making a change so you know what actually improved or broke.
- Use inspection tools such as `docker inspect`, `capsh --print`, `getenforce`, or scanner output as evidence rather than assumptions.
- When you tighten a control, force yourself to explain what new action is now blocked and how you would verify it.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Runtime Security](../12-runtime-security/README.md).
