# Crictl Debug

## Context & Problem
This topic explains how to inspect kubelet-facing container state through CRI tools. In production, this matters because fast recovery depends on collecting the right evidence before changing the system.

## First Principles
- Runtime stacks are layered and each layer has a different responsibility.
- High-level managers handle images, snapshots, and lifecycle; low-level runtimes turn an OCI bundle into a running process.
- The authoritative troubleshooting tool depends on which layer created and now manages the workload.

## Production Implementation
Use this topic to build an evidence hierarchy. Start with the least disruptive observation that can narrow the problem and only move to invasive tools once the current evidence no longer explains the symptom.

## Troubleshooting Approach
Follow the request path one layer at a time: kubelet or CLI, runtime manager, shim, low-level runtime, and then the process itself. Restart nothing until you know which hop is lying or failing.

## Evolution & Alternatives
Troubleshooting used to be dominated by host access and manual inspection. Modern platforms added more layers, which is why disciplined evidence collection is even more important today.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Decide which runtime interface owns the workload before you run any diagnostic command.
- Use layer-appropriate tools such as `crictl`, `ctr`, service status, or runtime logs instead of assuming Docker is the source of truth.
- Trace one workload from API call to running process so you can explain where state is stored at each hop.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Nerdctl Debug](../17-nerdctl-debug/README.md).
