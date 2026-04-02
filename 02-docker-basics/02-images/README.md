# Images

## Context & Problem
This topic explains how images are stored, identified, pulled, tagged, and inspected. In production, this matters because object-lifecycle mistakes quickly turn into accidental data loss, stale state, or misleading triage.
An image is not a running environment. It is an immutable template used to create one.

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
- `docker pull alpine:3.20`
- `docker run -d --name dk-lab alpine:3.20 sleep 300`
- `docker inspect dk-lab --format "{{.Config.Image}} {{.State.Status}}"`
- `docker exec dk-lab sh -c "id && hostname"`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- Which output proves image identity vs container runtime state?
- What production drift risk appears if image provenance is not verified?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Containers](../03-containers/README.md).
