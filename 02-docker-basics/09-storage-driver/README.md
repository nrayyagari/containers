# Storage Driver

## Context & Problem
This topic explains how Docker storage drivers implement copy-on-write layers on the host. In production, this matters because object-lifecycle mistakes quickly turn into accidental data loss, stale state, or misleading triage.

## First Principles
- Container storage has multiple lifecycles: image layers, writable layers, volumes, and external storage backends.
- Copy-on-write and overlay behavior can change both performance and the meaning of a write operation.
- Durability depends on where data lives, not on whether the application wrote it successfully once.

## Production Implementation
Map the command you run to the object it mutates: image, container, volume, network, or daemon state. Safe Docker operation comes from understanding which state is replaceable and which state must be preserved.

## Troubleshooting Approach
Ask three questions early: where does the data live, who owns it, and what path exposes it to the process? That separates permission problems from backend problems and durability problems from simple path mistakes.

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
- Which observation indicates storage-driver impact on behavior/performance?
- What failure pattern appears when storage-driver assumptions are wrong?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Compose YAML](../10-compose-yaml/README.md).
