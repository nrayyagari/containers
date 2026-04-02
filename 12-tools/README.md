# Tools

## What This Module Covers
This module maps common tools to the layer they expose: daemonless engines, OCI builders, CRI tools, registry tooling, debugging views, and migration helpers.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-podman](./01-podman/README.md): what Podman offers as a daemonless container engine.
- [02-buildah](./02-buildah/README.md): how Buildah builds OCI images without the Docker daemon model.
- [03-nerdctl](./03-nerdctl/README.md): how nerdctl exposes containerd features with familiar CLI semantics.
- [04-crictl](./04-crictl/README.md): how crictl speaks CRI for Kubernetes node debugging.
- [05-skopeo](./05-skopeo/README.md): how Skopeo inspects and copies images without pulling them locally.
- [06-docker-buildx](./06-docker-buildx/README.md): how Buildx unlocks BuildKit, multi-platform builds, and advanced caching.
- [07-kompose](./07-kompose/README.md): how Kompose translates Compose definitions into Kubernetes manifests.
- [08-ctop](./08-ctop/README.md): how ctop provides a top-like view of running containers.
- [09-dive](./09-dive/README.md): how Dive visualizes image layers and efficiency.
- [10-labs-container-toolkit](./10-labs-container-toolkit/README.md): how a practical toolkit ties these repo tools together.

## Move On When
- You can meet this module's main goal: Pick tools by backend authority, not by familiar syntax.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Advanced](../13-advanced/README.md).
