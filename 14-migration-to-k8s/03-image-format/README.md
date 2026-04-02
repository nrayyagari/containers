# Image Format

## Context & Problem
This topic explains how OCI image compatibility affects migration success. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.

## First Principles
- Image creation is additive: each build step leaves history, metadata, or filesystem state behind.
- Build-time decisions influence security, startup speed, cache reuse, and rollback safety after the image is published.
- Treat the image as a supply-chain artifact, not just a convenient tarball of files.

## Production Implementation
Use this topic to challenge a Docker-era assumption directly. In migration work, the risk is not ignorance of YAML; it is keeping the old mental model after the platform boundary has changed.

## Troubleshooting Approach
When builds or deployments behave unexpectedly, inspect the artifact and its metadata first. The runtime can only execute what the build and registry path actually delivered.

## Evolution & Alternatives
Migration thinking changed after dockershim removal and the rise of CRI-native nodes. The successful path now is to adopt Kubernetes-native operating concepts rather than preserve Docker-era habits behind new YAML.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `docker pull nginx:1.27-alpine`
- `docker image inspect nginx:1.27-alpine --format '{{.Id}} {{index .RepoDigests 0}}'`
- `skopeo inspect docker://docker.io/library/nginx:1.27-alpine 2>/dev/null | head -n 30 || true`
- `docker rmi nginx:1.27-alpine 2>/dev/null || true`

### What Success Looks Like
- Digest captured successfully.
- You can explain one rollout risk reduced by digest pinning.
- You documented one CI gate check for image promotion.

### Questions To Answer After The Lab
- Which digest/manifest evidence proves artifact immutability for rollout safety?
- What outage class is reduced by digest pinning during migration?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Pod Concept](../04-pod-concept/README.md).
