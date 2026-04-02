# Best Practices

## What This Module Covers
This module collects the practices that consistently reduce image bloat, rollout ambiguity, weak observability, and avoidable security risk. The focus is operational value, not style rules.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-image-size](./01-image-size/README.md): why smaller images improve transfer time, startup speed, and attack surface.
- [02-layer-optimization](./02-layer-optimization/README.md): how instruction ordering improves cache behavior and rebuild speed.
- [03-security-hardening](./03-security-hardening/README.md): how to reduce privilege and patch exposure.
- [04-multi-stage-builds](./04-multi-stage-builds/README.md): how multi-stage builds support clean runtime images.
- [05-healthchecks](./05-healthchecks/README.md): how to signal real application health without causing restart noise.
- [06-logging](./06-logging/README.md): how containers should emit logs for aggregation and analysis.
- [07-resource-limits](./07-resource-limits/README.md): how to set CPU and memory guardrails without hurting reliability.
- [08-immutable-tags](./08-immutable-tags/README.md): why mutable tags create deployment ambiguity.
- [09-minimal-base-images](./09-minimal-base-images/README.md): when slim, distroless, or scratch images are the right trade-off.
- [10-ci-cd-integration](./10-ci-cd-integration/README.md): how build, test, scan, sign, and publish steps fit into delivery pipelines.

## Move On When
- You can meet this module's main goal: Tie every best practice to a concrete operational benefit.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Troubleshooting](../11-troubleshooting/README.md).
