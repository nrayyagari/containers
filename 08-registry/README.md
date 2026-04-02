# Registry

## Context & Problem
Registries are often treated as passive storage, but they are an active part of the supply chain. Pull latency, image provenance, tag policy, cleanup behavior, and access control all influence production safety and rollout speed.

## First Principles
A registry stores blobs, manifests, tags, and metadata. Tags are pointers, manifests describe a specific artifact, and access control decides who may publish or pull it. Understanding those differences is what makes rollback and provenance credible.

## Production Implementation
Operate your registry as critical infrastructure, not as a background utility. Replication, mirrors, cleanup, access control, and trust workflows all influence whether nodes can pull the right artifact quickly and safely.

## Troubleshooting Approach
When image distribution fails, separate auth problems, name/tag problems, manifest problems, backend storage problems, and client cache problems. 'Image pull failed' is only a symptom; the registry path must be decomposed.

## Evolution & Alternatives
Container registries evolved from simple public image stores into OCI artifact platforms used for images, signatures, SBOMs, and attestations. The mechanism broadened, but the core need stayed the same: controlled distribution of immutable artifacts.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-docker-hub](./01-docker-hub/README.md): how the default public registry works and what its operational limits are.
- [02-private-registry](./02-private-registry/README.md): why organizations run their own registries for control, performance, and compliance.
- [03-harbor](./03-harbor/README.md): what Harbor adds on top of a plain registry for enterprise operations.
- [04-authentication](./04-authentication/README.md): how registries authorize pull and push actions.
- [05-push-pull](./05-push-pull/README.md): what actually happens during image upload and download.
- [06-mirrors-caching](./06-mirrors-caching/README.md): how mirrors reduce latency, rate limits, and upstream dependency.
- [07-content-trust](./07-content-trust/README.md): how signing and verification fit into registry workflows.
- [08-garbage-collection](./08-garbage-collection/README.md): how registries reclaim unreferenced blobs without breaking clients.
- [09-registry-api](./09-registry-api/README.md): what the registry API exposes for manifests, blobs, tags, and catalog operations.
- [10-artifact-management](./10-artifact-management/README.md): how OCI registries store more than container images.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After registry topics, move into orchestration so you can follow how those artifacts are selected, scheduled, and updated in a running system.
Continue with [Orchestration Basics](../09-orchestration-basics/README.md) when the topic map in this module feels operationally clear.
