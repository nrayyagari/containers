# Tools

## Context & Problem
The container toolchain is larger than the Docker CLI. Different tools are better for daemonless workflows, runtime debugging, registry inspection, build acceleration, or migration work, and choosing the wrong tool can slow both learning and incident response.

## First Principles
Every tool sits at a different layer. Some build images, some inspect registries, some speak CRI, some talk directly to containerd, and some are only for human visibility. Clear tool boundaries prevent false assumptions about what a command can prove.

## Production Implementation
Use tools deliberately, not because they feel familiar. The right tool is the one that talks to the authoritative layer without adding unnecessary mutation or abstraction.

## Troubleshooting Approach
When a command fails or shows incomplete state, ask what backend it speaks to. A Docker-like UX does not guarantee Docker semantics, and a runtime debugging tool may intentionally ignore images or volumes created through another interface.

## Evolution & Alternatives
The ecosystem expanded as container build, runtime, registry, and Kubernetes workflows decoupled. Learning the toolchain is less about memorizing commands and more about understanding which layer each tool exposes.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-podman](./01-podman/README.md): what Podman offers as a daemonless container engine.
- [02-buildah](./02-buildah/README.md): how Buildah builds OCI images without the Docker daemon model.
- [03-nerdctl](./03-nerdctl/README.md): how nerdctl exposes containerd features with familiar CLI semantics.
- [04-crictl](./04-crictl/README.md): how crictl speaks CRI for Kubernetes node debugging.
- [05-skopeo](./05-skopeo/README.md): how Skopeo inspects and copies images without pulling them locally.
- [06-docker-buildx](./06-docker-buildx/README.md): how Buildx unlocks BuildKit, multi-platform builds, and advanced caching.
- [07-kompose](./07-kompose/README.md): how Kompose translates Compose definitions into Kubernetes manifests.
- [08-ctop](./08-ctop/README.md): how ctop gives a live top-like view of running containers.
- [09-dive](./09-dive/README.md): how Dive visualizes image layers and efficiency.
- [10-labs-container-toolkit](./10-labs-container-toolkit/README.md): how a practical toolkit ties the repo tools together for daily engineering work.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After this module, the Advanced topics are easier to approach because you will already know which tools can show the low-level behavior those features depend on.
Continue with [Advanced](../13-advanced/README.md) when the topic map in this module feels operationally clear.
