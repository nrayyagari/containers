# Docker Basics

## Context & Problem
Many operational mistakes come from mixing up Docker objects. Engineers delete the wrong thing, assume data lives in the wrong layer, or diagnose a daemon problem as an application problem because the image/container/volume/network model is still fuzzy.

## First Principles
Docker gives you a user-friendly workflow, but it still maps to concrete objects: images, containers, volumes, networks, and daemon state. Each object has a different lifecycle, and production-safe operation depends on keeping those lifecycles separate in your head.

## Production Implementation
Connect every command to the object it changes. Before cleanup or rollout work, inspect the image, container, network, or volume explicitly so you know what is ephemeral, what is shared, and what will survive a restart.

## Troubleshooting Approach
Start with inspection commands and logs, not forceful restarts. Many Docker incidents are really object-lifecycle mistakes, stale configuration, or host-level daemon problems.

## Evolution & Alternatives
Docker popularized containers by packaging runtime, build, and UX together. Modern platforms often separate those concerns, but the Docker object model is still the fastest way to learn the operational basics.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-cli-basics](./01-cli-basics/README.md) | [Lab](./01-cli-basics/LAB.md): how Docker CLI commands map to object lifecycle operations and inspection workflows.
- [02-images](./02-images/README.md) | [Lab](./02-images/LAB.md): how images are stored, identified, pulled, tagged, and inspected.
- [03-containers](./03-containers/README.md) | [Lab](./03-containers/LAB.md): how a container moves through create, start, stop, restart, and remove.
- [04-volumes](./04-volumes/README.md) | [Lab](./04-volumes/LAB.md): how Docker keeps data outside an ephemeral container filesystem.
- [05-networking-basics](./05-networking-basics/README.md) | [Lab](./05-networking-basics/LAB.md): how Docker connects containers using bridge, host, none, and user-defined networks.
- [06-dockerfile](./06-dockerfile/README.md) | [Lab](./06-dockerfile/LAB.md): how a Dockerfile defines the filesystem and runtime defaults of an image.
- [07-docker-compose](./07-docker-compose/README.md) | [Lab](./07-docker-compose/LAB.md): how Compose describes and runs multi-container applications.
- [08-docker-daemon](./08-docker-daemon/README.md) | [Lab](./08-docker-daemon/LAB.md): how the Docker daemon brokers build, image, network, and container operations.
- [09-storage-driver](./09-storage-driver/README.md) | [Lab](./09-storage-driver/LAB.md): how Docker storage drivers implement copy-on-write layers on the host.
- [10-compose-yaml](./10-compose-yaml/README.md) | [Lab](./10-compose-yaml/LAB.md): how the Compose file schema expresses services, networks, volumes, and runtime settings.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After this module, move to Image Building so you understand how the artifacts behind those objects are created and controlled.
Continue with [Image Building](../03-image-building/README.md) when the topic map in this module feels operationally clear.
