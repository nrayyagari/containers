# Cli Basics

## Context & Problem
This topic explains how Docker CLI commands map to object lifecycle operations and inspection workflows. In production, this matters because object-lifecycle mistakes quickly turn into accidental data loss, stale state, or misleading triage.

## First Principles
- Docker operations make sense only when you keep images, containers, volumes, networks, and daemon state separate in your head.
- Some Docker commands create objects, some mutate them, and some only reveal existing state; confusing those roles creates most day-2 mistakes.
- The safest Docker workflow is inspection first, change second, cleanup last.

## Production Implementation
Map the command you run to the object it mutates: image, container, volume, network, or daemon state. Safe Docker operation comes from understanding which state is replaceable and which state must be preserved.

## Troubleshooting Approach
Start with direct evidence at the layer this topic controls, then expand outward only if the observed state matches expectations.

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
- Which Docker CLI command in this lab gave the most authoritative state?
- What mistake occurs when teams rely only on `docker ps` snapshots?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Images](../02-images/README.md).
