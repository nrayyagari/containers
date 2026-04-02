# Troubleshooting

## What This Module Covers
This module is about asking the next correct question during a container incident. It covers logs, process inspection, network debugging, runtime tools, metrics, image inspection, and cleanup.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-logs](./01-logs/README.md): how container logs and engine logs provide the first evidence stream.
- [02-inside-container](./02-inside-container/README.md): how to inspect a container process, filesystem, and namespace state safely.
- [03-network-debugging](./03-network-debugging/README.md): how to narrow connectivity problems to DNS, routing, firewall, or app behavior.
- [04-resource-issues](./04-resource-issues/README.md): how to diagnose OOM kills, throttling, and pressure-related slowdowns.
- [05-process-analysis](./05-process-analysis/README.md): how to understand process trees, parents, and signals inside containers.
- [06-disk-space](./06-disk-space/README.md): how image layers, writable layers, and volumes consume host storage.
- [07-dns-issues](./07-dns-issues/README.md): how resolver config and upstream failures affect container lookups.
- [08-exit-codes](./08-exit-codes/README.md): how process exit codes separate app crashes from platform problems.
- [09-core-dumps](./09-core-dumps/README.md): how to capture crash data safely.
- [10-tools-dive-ctop-sysdig](./10-tools-dive-ctop-sysdig/README.md): when to use ctop, Dive, or Sysdig for deeper inspection.
- [11-strace-ltrace](./11-strace-ltrace/README.md): how syscall and library-call tracing expose hidden failures.
- [12-tcpdump-wireshark](./12-tcpdump-wireshark/README.md): how packet capture proves where traffic is lost or transformed.
- [13-htop-top](./13-htop-top/README.md): what CPU, memory, and process views tell you during a live incident.
- [14-sysdig-falco](./14-sysdig-falco/README.md): how syscall monitoring and rules detect suspicious runtime behavior.
- [15-prometheus-metrics](./15-prometheus-metrics/README.md): how time-series metrics complement shell-based debugging.
- [16-crictl-debug](./16-crictl-debug/README.md): how to inspect kubelet-facing container state through CRI tools.
- [17-nerdctl-debug](./17-nerdctl-debug/README.md): how to debug containerd-managed workloads with a Docker-like CLI.
- [18-dive-image-analysis](./18-dive-image-analysis/README.md): how to inspect image layers and wasted space before runtime.
- [19-cosign-signature-verification](./19-cosign-signature-verification/README.md): how to verify image signatures before you trust an artifact.
- [20-garbage-collection-cleanup](./20-garbage-collection-cleanup/README.md): how to reclaim space safely without deleting needed artifacts.

## Move On When
- You can meet this module's main goal: Use the least disruptive evidence source that answers the next question.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Tools](../12-tools/README.md).
