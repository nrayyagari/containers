# Image Building

## What This Module Covers
This module turns image building into an engineering problem instead of a packaging afterthought. It covers Dockerfiles, layer behavior, base-image choice, tagging, secrets, and registry interaction.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-dockerfile-basics](./01-dockerfile-basics/README.md) | [Lab](./01-dockerfile-basics/LAB.md): how Dockerfile order and defaults shape the final image.
- [02-instructions](./02-instructions/README.md) | [Lab](./02-instructions/LAB.md): what common Dockerfile instructions do at build time and run time.
- [03-multi-stage-builds](./03-multi-stage-builds/README.md) | [Lab](./03-multi-stage-builds/LAB.md): how to split build and runtime stages to reduce size and risk.
- [04-layer-caching](./04-layer-caching/README.md) | [Lab](./04-layer-caching/LAB.md): how cache hits and misses affect build speed and reproducibility.
- [05-base-images](./05-base-images/README.md) | [Lab](./05-base-images/LAB.md): how base image choice changes size, compatibility, and attack surface.
- [06-best-practices](./06-best-practices/README.md) | [Lab](./06-best-practices/LAB.md): how to build images that are small, reproducible, and maintainable.
- [07-registries](./07-registries/README.md) | [Lab](./07-registries/LAB.md): how builds and runtimes interact with image registries.
- [08-tags](./08-tags/README.md) | [Lab](./08-tags/LAB.md): how tag strategy affects traceability and rollback safety.
- [09-build-arguments](./09-build-arguments/README.md) | [Lab](./09-build-arguments/LAB.md): how ARG values affect a build without becoming runtime environment variables.
- [10-build-secrets](./10-build-secrets/README.md) | [Lab](./10-build-secrets/LAB.md): how BuildKit passes sensitive material without baking it into layers.

## Move On When
- You can meet this module's main goal: Be able to explain exactly what is in an image and why.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Container Runtimes](../04-container-runtimes/README.md).
