# 03 Image Building

## Context & Problem
Weak image build practices increase attack surface, CI time, and production drift.

## First Principles
Dockerfile instruction order and base image selection drive artifact quality.

## Production Implementation
Use deterministic builds and inspect output before promoting images.

## Troubleshooting Approach
For build regressions, compare layer history and build context changes first.

## Topic Map
- [01-dockerfile-basics](./01-dockerfile-basics/README.md) | [Lab](./01-dockerfile-basics/LAB.md)
- [02-instructions](./02-instructions/README.md) | [Lab](./02-instructions/LAB.md)
- [03-multi-stage-builds](./03-multi-stage-builds/README.md) | [Lab](./03-multi-stage-builds/LAB.md)
- [04-layer-caching](./04-layer-caching/README.md) | [Lab](./04-layer-caching/LAB.md)
- [05-base-images](./05-base-images/README.md) | [Lab](./05-base-images/LAB.md)
- [06-best-practices](./06-best-practices/README.md) | [Lab](./06-best-practices/LAB.md)
- [07-registries](./07-registries/README.md) | [Lab](./07-registries/LAB.md)
- [08-tags](./08-tags/README.md) | [Lab](./08-tags/LAB.md)
- [09-build-arguments](./09-build-arguments/README.md) | [Lab](./09-build-arguments/LAB.md)
- [10-build-secrets](./10-build-secrets/README.md) | [Lab](./10-build-secrets/LAB.md)

## Zero-Confusion Summary
- What it is:
  - A structured module with practice-first learning.
- What it is not:
  - It is not theory-only reading material.
- When to use:
  - Use it sequentially and complete each topic lab.
