# Best Practices

## Context & Problem
Best practices are really lessons paid for by outages, debugging time, and unnecessary cloud spend. This module turns those lessons into repeatable habits so the same mistakes are not rediscovered during every migration or incident.

## First Principles
A good container practice usually reduces one of four things: ambiguity, blast radius, startup time, or recovery time. If a so-called best practice does not improve one of those, it is probably style guidance rather than production guidance.

## Production Implementation
Use this module to tighten the feedback loop between build quality, runtime behavior, and incident cost. Small improvements here compound because the same images and deployment patterns are reused everywhere.

## Troubleshooting Approach
When systems are unreliable, look for broken fundamentals first: oversized images, weak health signals, missing limits, mutable tags, poor logs, or insecure defaults. Those weaknesses tend to amplify every other bug.

## Evolution & Alternatives
What counts as a best practice changes as tooling improves, but the direction is stable: smaller artifacts, less privilege, clearer signals, stronger provenance, and more deterministic rollout behavior.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-image-size](./01-image-size/README.md): why smaller images improve transfer time, startup speed, attack surface, and cache efficiency.
- [02-layer-optimization](./02-layer-optimization/README.md): how instruction ordering and file grouping improve cache behavior and rebuild speed.
- [03-security-hardening](./03-security-hardening/README.md): how to reduce privileges, patch exposure, and supply-chain risk.
- [04-multi-stage-builds](./04-multi-stage-builds/README.md): how multi-stage builds turn a best practice into a repeatable delivery pattern.
- [05-healthchecks](./05-healthchecks/README.md): how to signal application health accurately without causing restart storms.
- [06-logging](./06-logging/README.md): how containers should emit logs so platforms can aggregate and query them.
- [07-resource-limits](./07-resource-limits/README.md): how to size CPU and memory guardrails without sabotaging reliability.
- [08-immutable-tags](./08-immutable-tags/README.md): why mutable tags such as latest create ambiguity in deployments.
- [09-minimal-base-images](./09-minimal-base-images/README.md): when slim, distroless, or scratch images are the right trade-off.
- [10-ci-cd-integration](./10-ci-cd-integration/README.md): how build, test, scan, sign, and publish steps fit into delivery pipelines.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After this module, use Troubleshooting and Tools to practice how these standards affect real diagnosis work when something goes wrong.
Continue with [Troubleshooting](../11-troubleshooting/README.md) when the topic map in this module feels operationally clear.
