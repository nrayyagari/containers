# Container Runtimes

## Context & Problem
Runtime stack internals from manager to low-level execution.

## First Principles
OCI defines contract; runtime manager orchestrates lifecycle; low-level runtime executes process.

## Production Implementation
Troubleshoot by mapping symptom to correct runtime layer using process and CRI evidence.

## Troubleshooting Approach
Follow chain: control plane to CRI to runtime manager to low-level runtime.

## Evolution & Alternatives
Dockershim removal made CRI knowledge mandatory for Kubernetes operations.

## Next Steps
Proceed to migration-to-k8s and map runtime knowledge to cluster operations.

## Topic Map
- [01-runc](./01-runc/README.md) | [Lab](./01-runc/LAB.md)
- [02-containerd](./02-containerd/README.md) | [Lab](./02-containerd/LAB.md)
- [03-cri](./03-cri/README.md) | [Lab](./03-cri/LAB.md)
- [04-crio](./04-crio/README.md) | [Lab](./04-crio/LAB.md)
- [05-docker-vs-containerd](./05-docker-vs-containerd/README.md) | [Lab](./05-docker-vs-containerd/LAB.md)
- [06-low-level-runtime](./06-low-level-runtime/README.md) | [Lab](./06-low-level-runtime/LAB.md)
- [07-high-level-runtime](./07-high-level-runtime/README.md) | [Lab](./07-high-level-runtime/LAB.md)
- [08-shim-process](./08-shim-process/README.md) | [Lab](./08-shim-process/LAB.md)
- [09-oci-spec](./09-oci-spec/README.md) | [Lab](./09-oci-spec/LAB.md)
- [10-runtime-classes](./10-runtime-classes/README.md) | [Lab](./10-runtime-classes/LAB.md)

## Zero-Confusion Summary
- Read topic README first.
- Run LAB step-by-step in order.
- Mark lab complete only when Verify and Answer Key pass criteria are satisfied.
