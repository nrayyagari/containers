# crictl

## Context & Problem
This topic explains how crictl speaks CRI for Kubernetes node debugging. In production, this matters because tool choice determines which layer you can actually observe and which assumptions remain hidden.

## First Principles
- Runtime stacks are layered and each layer has a different responsibility.
- High-level managers handle images, snapshots, and lifecycle; low-level runtimes turn an OCI bundle into a running process.
- The authoritative troubleshooting tool depends on which layer created and now manages the workload.

## Production Implementation
Use the tool because its backend matches the system layer you care about, not because its UX is familiar. Good operators choose tools the same way they choose APIs: by authority and scope.

## Troubleshooting Approach
Follow the request path one layer at a time: kubelet or CLI, runtime manager, shim, low-level runtime, and then the process itself. Restart nothing until you know which hop is lying or failing.

## Evolution & Alternatives
The ecosystem diversified as build, runtime, registry, and Kubernetes concerns separated. Tool sprawl is the price of specialization, so clarity about scope matters more than CLI memorization.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Decide which runtime interface owns the workload before you run any diagnostic command.
- Use layer-appropriate tools such as `crictl`, `ctr`, service status, or runtime logs instead of assuming Docker is the source of truth.
- Trace one workload from API call to running process so you can explain where state is stored at each hop.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Skopeo](../05-skopeo/README.md).
