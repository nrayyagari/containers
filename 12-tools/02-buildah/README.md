# Buildah

## Context & Problem
This topic explains how Buildah builds OCI images without the Docker daemon model. In production, this matters because tool choice determines which layer you can actually observe and which assumptions remain hidden.

## First Principles
- Image creation is additive: each build step leaves history, metadata, or filesystem state behind.
- Build-time decisions influence security, startup speed, cache reuse, and rollback safety after the image is published.
- Treat the image as a supply-chain artifact, not just a convenient tarball of files.

## Production Implementation
Use the tool because its backend matches the system layer you care about, not because its UX is familiar. Good operators choose tools the same way they choose APIs: by authority and scope.

## Troubleshooting Approach
When builds or deployments behave unexpectedly, inspect the artifact and its metadata first. The runtime can only execute what the build and registry path actually delivered.

## Evolution & Alternatives
The ecosystem diversified as build, runtime, registry, and Kubernetes concerns separated. Tool sprawl is the price of specialization, so clarity about scope matters more than CLI memorization.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Inspect the artifact, not just the Dockerfile: use `docker history`, `docker inspect`, or registry metadata to prove what shipped.
- Practice rebuilding after one small change so you can observe cache behavior and the resulting metadata difference.
- Treat tags as references and verify the immutable digest whenever traceability matters.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [nerdctl](../03-nerdctl/README.md).
