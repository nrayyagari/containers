# Registry

## What This Module Covers
This module treats the registry as part of the supply chain, not as passive storage. It covers tags, manifests, auth, mirrors, garbage collection, APIs, and OCI artifacts.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-docker-hub](./01-docker-hub/README.md) | [Lab](./01-docker-hub/LAB.md): how the default public registry works and what its limits are.
- [02-private-registry](./02-private-registry/README.md) | [Lab](./02-private-registry/LAB.md): why organizations run private registries for control and compliance.
- [03-harbor](./03-harbor/README.md) | [Lab](./03-harbor/LAB.md): what Harbor adds on top of a plain registry.
- [04-authentication](./04-authentication/README.md) | [Lab](./04-authentication/LAB.md): how registries authorize pull and push actions.
- [05-push-pull](./05-push-pull/README.md) | [Lab](./05-push-pull/LAB.md): what actually happens during image upload and download.
- [06-mirrors-caching](./06-mirrors-caching/README.md) | [Lab](./06-mirrors-caching/LAB.md): how mirrors reduce latency and upstream dependency.
- [07-content-trust](./07-content-trust/README.md) | [Lab](./07-content-trust/LAB.md): how signing and verification fit into registry workflows.
- [08-garbage-collection](./08-garbage-collection/README.md) | [Lab](./08-garbage-collection/LAB.md): how registries reclaim unreferenced blobs safely.
- [09-registry-api](./09-registry-api/README.md) | [Lab](./09-registry-api/LAB.md): what the registry API exposes for manifests, blobs, and tags.
- [10-artifact-management](./10-artifact-management/README.md) | [Lab](./10-artifact-management/LAB.md): how OCI registries store more than container images.

## Move On When
- You can meet this module's main goal: Know what object is being pulled, by whom, and why.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Orchestration Basics](../09-orchestration-basics/README.md).
