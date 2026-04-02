# Troubleshooting

## Context & Problem
Container incidents become noisy fast because several layers can fail at once: application, runtime, network, storage, and host. Troubleshooting works only when you build an evidence hierarchy instead of jumping between random commands.

## First Principles
Good debugging starts by proving where the failure is not. Logs, process state, resource state, packet evidence, image contents, runtime state, and signatures each answer different questions. Mixing them without a hypothesis just creates more noise.

## Production Implementation
Use the least disruptive tool that can answer the next question. Read state before mutating state, and always decide whether the authoritative view lives in the application, the container runtime, the node, or the control plane.

## Troubleshooting Approach
This module is the troubleshooting approach. Collect timelines, identify the first hard signal, then move outward layer by layer until the symptom and mechanism line up. Restarting components should be the end of the investigation, not the beginning.

## Evolution & Alternatives
As platforms grew more layered, debugging moved from 'SSH in and look around' to combining node tools, runtime tools, image tools, metrics, and signatures. The core discipline, however, is still simple: trust evidence over intuition.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-logs](./01-logs/README.md): how to use stdout and stderr, container logs, and engine logs as the first evidence stream.
- [02-inside-container](./02-inside-container/README.md): how to inspect a container process, filesystem, and namespace state safely.
- [03-network-debugging](./03-network-debugging/README.md): how to narrow connectivity problems to DNS, routing, firewall, or application behavior.
- [04-resource-issues](./04-resource-issues/README.md): how to diagnose OOM kills, CPU throttling, and pressure-related slowdowns.
- [05-process-analysis](./05-process-analysis/README.md): how to understand process trees, parents, and signals inside containers.
- [06-disk-space](./06-disk-space/README.md): how image layers, writable layers, and volumes consume host storage.
- [07-dns-issues](./07-dns-issues/README.md): how resolver config, embedded DNS, and upstream failures affect container name lookups.
- [08-exit-codes](./08-exit-codes/README.md): how process exit codes separate app crashes from platform problems.
- [09-core-dumps](./09-core-dumps/README.md): how to capture crash data without losing containment or filling disks.
- [10-tools-dive-ctop-sysdig](./10-tools-dive-ctop-sysdig/README.md): when to use ctop for visibility and sysdig for deeper event inspection.
- [11-strace-ltrace](./11-strace-ltrace/README.md): how syscall and library-call tracing expose hidden runtime failures.
- [12-tcpdump-wireshark](./12-tcpdump-wireshark/README.md): how packet capture proves where traffic is lost or transformed.
- [13-htop-top](./13-htop-top/README.md): what CPU, memory, and process views tell you during a live incident.
- [14-sysdig-falco](./14-sysdig-falco/README.md): how system call monitoring and rules detect suspicious runtime behavior.
- [15-prometheus-metrics](./15-prometheus-metrics/README.md): how time-series metrics complement point-in-time shell debugging.
- [16-crictl-debug](./16-crictl-debug/README.md): how to inspect kubelet-facing container state through CRI tools.
- [17-nerdctl-debug](./17-nerdctl-debug/README.md): how to debug containerd-managed workloads with a Docker-like CLI.
- [18-dive-image-analysis](./18-dive-image-analysis/README.md): how to inspect image layers and wasted space before runtime.
- [19-cosign-signature-verification](./19-cosign-signature-verification/README.md): how to verify signatures before trusting an image.
- [20-garbage-collection-cleanup](./20-garbage-collection-cleanup/README.md): how to reclaim space safely without deleting required artifacts.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After this module, the Tools section will make more sense because you will know what question each tool is actually supposed to answer.
Continue with [Tools](../12-tools/README.md) when the topic map in this module feels operationally clear.
