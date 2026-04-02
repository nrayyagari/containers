# Docker To Containerd Lab

## Goal
Prove the difference between Docker CLI visibility and CRI runtime visibility used by Kubernetes.

## Prerequisites
- Linux host with Docker, containerd, and crictl installed.
- Access to read kubelet runtime endpoint settings.

## Steps
1. Check runtime services.
   COMMAND: systemctl status docker --no-pager || true
   COMMAND: systemctl status containerd --no-pager || true
2. Compare image visibility.
   COMMAND: docker pull alpine:3.20
   COMMAND: docker images | grep alpine
   COMMAND: crictl pull alpine:3.20 || true
   COMMAND: crictl images | grep alpine || true
3. Compare running container visibility.
   COMMAND: docker run -d --name runtime-compare alpine:3.20 sleep 180
   COMMAND: docker ps -a | grep runtime-compare
   COMMAND: crictl ps -a || true
4. Record one case where Docker output and CRI output differ.

## Expected Observations
- containerd and/or Docker service status is visible.
- Docker and CRI commands may not show identical workload views.
- You can explain which view is authoritative for kubelet-managed workloads.

## Verify
- You identified the node runtime command set to use in Kubernetes incidents.
- You captured evidence for Docker-vs-CRI view differences.
- You documented one diagnostic rule for your runbook.

## Cleanup
- COMMAND: docker rm -f runtime-compare 2>/dev/null || true

## Concept Check
- Why can docker ps mislead you on a Kubernetes node?
- Which command set should SREs trust first for kubelet runtime issues?
- What incident delay occurs when teams debug the wrong runtime layer?

## Why This Lab Proves Understanding
- You validated behavior using both Docker and CRI evidence.

## Answer Key
Pass when all Verify points are satisfied and cleanup is complete.
