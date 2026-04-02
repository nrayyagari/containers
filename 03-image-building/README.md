# Image Building

## Context & Problem
Image problems are supply-chain problems. A careless build can produce oversized images, hidden secrets, slow deployments, inconsistent environments, or artifacts you cannot explain during an incident.

## First Principles
An image is an immutable artifact built in layers. Instruction order, build context, base-image choice, metadata, and cache behavior all shape the artifact that eventually lands in production.

## Production Implementation
Treat image creation as an engineering discipline, not a packaging afterthought. Make inputs explicit, keep layers intentional, and inspect what actually shipped before trusting a tag in CI/CD.

## Troubleshooting Approach
When an image behaves unexpectedly, inspect its Dockerfile, history, build arguments, and registry metadata before blaming runtime or orchestration. Many runtime surprises are baked into the image itself.

## Evolution & Alternatives
BuildKit, multi-stage builds, and better registry workflows changed image creation from a monolithic Dockerfile exercise into a reproducible build pipeline. The core idea stayed the same: build the smallest trustworthy artifact you can explain.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-dockerfile-basics](./01-dockerfile-basics/README.md) | [Lab](./01-dockerfile-basics/LAB.md): how Dockerfile order and defaults shape the final image.
- [02-instructions](./02-instructions/README.md) | [Lab](./02-instructions/LAB.md): what common Dockerfile instructions really do at build time and at run time.
- [03-multi-stage-builds](./03-multi-stage-builds/README.md) | [Lab](./03-multi-stage-builds/LAB.md): how separate build and runtime stages shrink images and remove toolchains.
- [04-layer-caching](./04-layer-caching/README.md) | [Lab](./04-layer-caching/LAB.md): how layer cache hits and misses affect build speed and reproducibility.
- [05-base-images](./05-base-images/README.md) | [Lab](./05-base-images/LAB.md): how the first FROM determines compatibility, attack surface, size, and debugging options.
- [06-best-practices](./06-best-practices/README.md) | [Lab](./06-best-practices/LAB.md): how to build images that are small, reproducible, secure, and maintainable.
- [07-registries](./07-registries/README.md) | [Lab](./07-registries/LAB.md): how builders and runtimes interact with registries during push and pull.
- [08-tags](./08-tags/README.md) | [Lab](./08-tags/LAB.md): how image tags affect versioning, traceability, and rollback safety.
- [09-build-arguments](./09-build-arguments/README.md) | [Lab](./09-build-arguments/LAB.md): how ARG values influence builds without becoming container environment variables.
- [10-build-secrets](./10-build-secrets/README.md) | [Lab](./10-build-secrets/LAB.md): how BuildKit passes sensitive material without baking it into image layers.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After this module, move to Container Runtimes so you can follow the artifact from build output to actual process execution.
Continue with [Container Runtimes](../04-container-runtimes/README.md) when the topic map in this module feels operationally clear.
