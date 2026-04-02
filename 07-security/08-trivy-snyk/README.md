# Trivy and Snyk

## Context & Problem
This topic explains how common image scanners differ in workflow, data sources, and trade-offs. In production, this matters because container security fails when teams treat one control as sufficient instead of layering identity, policy, and trust.

## First Principles
- A scanner is only as useful as the data source, matching logic, and workflow discipline behind it.
- Different scanners may report different results for the same image because they model packages, layers, and vulnerability databases differently.
- The goal is not to collect alerts; it is to decide which risks are real enough to block, patch, or document.

## Production Implementation
Treat this control as one layer in a defense-in-depth model. Production hardening means preserving just enough privilege for the workload to function and then proving that the control you added is actually enforced.

## Troubleshooting Approach
Start with direct evidence at the layer this topic controls, then expand outward only if the observed state matches expectations.

## Evolution & Alternatives
Container security shifted from 'don't run everything as root' into a broader supply-chain and runtime-hardening discipline. The deeper improvement was treating trust as an end-to-end property rather than a runtime-only property.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Practice on a disposable workload or host so you can observe before-and-after behavior without cleanup risk.
- Capture one direct signal that proves the mechanism and one failure mode that would invalidate your assumption.
- Explain the topic back in plain language before moving on.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Image Signing](../09-image-signing/README.md).
