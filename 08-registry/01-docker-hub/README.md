# Docker Hub

## Context & Problem
This topic explains how the default public registry works and what its operational limits are. In production, this matters because every push and pull is part of your software supply chain, not just a file copy.

## First Principles
- A registry stores immutable blobs and manifests, while tags are mutable references that point at those manifests.
- Distribution, authentication, retention, and trust are all separate concerns even though they meet at the same registry endpoint.
- Registry literacy matters because deployment safety depends on knowing exactly what object a client is pulling and why it is allowed to do so.

## Production Implementation
Operate the registry as part of the delivery path. Tag policy, auth, mirroring, garbage collection, and signing workflows all influence whether nodes can fetch the right artifact quickly and safely.

## Troubleshooting Approach
Start with direct evidence at the layer this topic controls, then expand outward only if the observed state matches expectations.

## Evolution & Alternatives
Registries evolved from image stores into OCI artifact platforms. That change matters because supply-chain metadata now travels beside the image instead of living in separate systems.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Inspect one image by both tag and digest so you can see the difference between a mutable reference and an immutable artifact.
- Use registry-aware tooling such as `skopeo inspect`, `curl /v2/`, or your registry UI to verify what manifests, tags, and auth decisions actually exist.
- Practice a small push, pull, or retention scenario and explain which registry object changed and which did not.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Private Registry](../02-private-registry/README.md).
