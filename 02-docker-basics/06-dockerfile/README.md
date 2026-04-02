# Dockerfile

## Context & Problem
This topic explains how a Dockerfile defines the filesystem and runtime defaults of an image. In production, this matters because object-lifecycle mistakes quickly turn into accidental data loss, stale state, or misleading triage.
A Dockerfile may look like a shell script in places, but it is really a declarative build recipe whose ordering affects the final artifact.

## First Principles
- Image creation is additive: each build step leaves history, metadata, or filesystem state behind.
- Build-time decisions influence security, startup speed, cache reuse, and rollback safety after the image is published.
- Treat the image as a supply-chain artifact, not just a convenient tarball of files.

## Production Implementation
Map the command you run to the object it mutates: image, container, volume, network, or daemon state. Safe Docker operation comes from understanding which state is replaceable and which state must be preserved.

## Troubleshooting Approach
When builds or deployments behave unexpectedly, inspect the artifact and its metadata first. The runtime can only execute what the build and registry path actually delivered.

## Evolution & Alternatives
Docker's user experience made containers mainstream, but many production stacks now split build, runtime, and orchestration concerns across separate tools. Learning Docker remains useful because it provides the cleanest introduction to the object model.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `docker build -t dbk-lab:latest /tmp/dbk-lab`
- `docker run --rm dbk-lab:latest`
- `docker image inspect dbk-lab:latest | head -n 20`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- Which Dockerfile instruction in your lab most impacted runtime behavior?
- What security risk appears from copying unnecessary build context files?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Docker Compose](../07-docker-compose/README.md).
