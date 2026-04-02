# Docker Basics

## What This Module Covers
This module covers the objects Docker manages: images, containers, volumes, networks, Dockerfiles, Compose files, and daemon state. The point is to separate those lifecycles clearly enough that cleanup, rollout, and debugging decisions become obvious.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-cli-basics](./01-cli-basics/README.md) | [Lab](./01-cli-basics/LAB.md): how Docker CLI commands map to object lifecycle operations.
- [02-images](./02-images/README.md) | [Lab](./02-images/LAB.md): how images are pulled, tagged, stored, and inspected.
- [03-containers](./03-containers/README.md) | [Lab](./03-containers/LAB.md): how containers move through create, start, stop, and remove.
- [04-volumes](./04-volumes/README.md) | [Lab](./04-volumes/LAB.md): how Docker keeps data outside the container writable layer.
- [05-networking-basics](./05-networking-basics/README.md) | [Lab](./05-networking-basics/LAB.md): how Docker connects containers with built-in network modes.
- [06-dockerfile](./06-dockerfile/README.md) | [Lab](./06-dockerfile/LAB.md): how a Dockerfile defines image content and runtime defaults.
- [07-docker-compose](./07-docker-compose/README.md) | [Lab](./07-docker-compose/LAB.md): how Compose describes and runs multi-container applications.
- [08-docker-daemon](./08-docker-daemon/README.md) | [Lab](./08-docker-daemon/LAB.md): how the Docker daemon brokers build and runtime operations.
- [09-storage-driver](./09-storage-driver/README.md) | [Lab](./09-storage-driver/LAB.md): how copy-on-write storage drivers back Docker layers.
- [10-compose-yaml](./10-compose-yaml/README.md) | [Lab](./10-compose-yaml/LAB.md): how Compose YAML expresses services, networks, and volumes.

## Move On When
- You can meet this module's main goal: Know what object you are changing before you run the command.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Image Building](../03-image-building/README.md).
