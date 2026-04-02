# Container Runtimes

## Context & Problem
Runtime incidents are hard when the stack is still blurry. Engineers often say 'Docker is broken' when the actual problem is in kubelet-to-CRI communication, containerd state, the OCI bundle, or the low-level runtime.

## First Principles
A runtime stack has layers. OCI defines contracts, high-level managers handle images and lifecycle, low-level runtimes create the process, and Kubernetes speaks to the stack through CRI. Understanding those boundaries is what makes node-level debugging tractable.

## Production Implementation
Debug by following the chain from control plane to runtime manager to low-level executor. If you skip a layer, you will restart the wrong component or trust the wrong source of truth.

## Troubleshooting Approach
Always decide which API surface is authoritative for the workload you are investigating. Docker, `crictl`, `ctr`, and kubelet can show different slices of reality depending on who created the container and which interface you are using.

## Evolution & Alternatives
The runtime world shifted from Docker-centric node plumbing to CRI-native stacks such as containerd and CRI-O. That change made the boundaries clearer, but it also made it mandatory for operators to understand them.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-runc](./01-runc/README.md) | [Lab](./01-runc/LAB.md): how the low-level OCI runtime creates the container process from a bundle.
- [02-containerd](./02-containerd/README.md) | [Lab](./02-containerd/LAB.md): how containerd manages images, snapshots, tasks, and runtime integration.
- [03-cri](./03-cri/README.md) | [Lab](./03-cri/LAB.md): how kubelet talks to runtimes through the Container Runtime Interface.
- [04-crio](./04-crio/README.md) | [Lab](./04-crio/LAB.md): how CRI-O provides a Kubernetes-focused runtime implementation.
- [05-docker-vs-containerd](./05-docker-vs-containerd/README.md) | [Lab](./05-docker-vs-containerd/LAB.md): how Docker and containerd differ in scope, UX, and Kubernetes fit.
- [06-low-level-runtime](./06-low-level-runtime/README.md) | [Lab](./06-low-level-runtime/LAB.md): what low-level runtimes do versus higher-level managers.
- [07-high-level-runtime](./07-high-level-runtime/README.md) | [Lab](./07-high-level-runtime/LAB.md): what higher-level runtimes add around images, snapshots, shims, and lifecycle.
- [08-shim-process](./08-shim-process/README.md) | [Lab](./08-shim-process/LAB.md): why shims sit between the runtime manager and individual containers.
- [09-oci-spec](./09-oci-spec/README.md) | [Lab](./09-oci-spec/LAB.md): how OCI specifications standardize image, runtime, and distribution behavior.
- [10-runtime-classes](./10-runtime-classes/README.md) | [Lab](./10-runtime-classes/LAB.md): how Kubernetes selects different runtime handlers per workload.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After this module, the networking, storage, security, and Kubernetes migration topics will make more sense because you will know who is actually launching the workload.
Continue with [Networking](../05-networking/README.md) when the topic map in this module feels operationally clear.
