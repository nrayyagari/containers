# Private Registry

## Context & Problem
This topic explains why organizations run their own registries for control, performance, and compliance. In production, this matters because every push and pull is part of your software supply chain, not just a file copy.

## First Principles
- Image creation is additive: each build step leaves history, metadata, or filesystem state behind.
- Build-time decisions influence security, startup speed, cache reuse, and rollback safety after the image is published.
- Treat the image as a supply-chain artifact, not just a convenient tarball of files.

## Production Implementation
Operate the registry as part of the delivery path. Tag policy, auth, mirroring, garbage collection, and signing workflows all influence whether nodes can fetch the right artifact quickly and safely.

## Troubleshooting Approach
When builds or deployments behave unexpectedly, inspect the artifact and its metadata first. The runtime can only execute what the build and registry path actually delivered.

## Evolution & Alternatives
Registries evolved from image stores into OCI artifact platforms. That change matters because supply-chain metadata now travels beside the image instead of living in separate systems.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Inspect the artifact, not just the Dockerfile: use `docker history`, `docker inspect`, or registry metadata to prove what shipped.
- Practice rebuilding after one small change so you can observe cache behavior and the resulting metadata difference.
- Treat tags as references and verify the immutable digest whenever traceability matters.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Harbor](../03-harbor/README.md).
