# Docker to containerd Lab

## Goal
Compare Docker-centric commands with CRI/containerd commands so you can debug Kubernetes nodes correctly.

## Prerequisites
- Linux host with Docker installed
- `containerd` and `crictl` available (or a Kubernetes node)

## Steps
1. Check runtime services:
   ```bash
   systemctl status docker --no-pager || true
   systemctl status containerd --no-pager || true
   ```
2. Pull and list an image with Docker:
   ```bash
   docker pull alpine:3.20
   docker images | grep alpine
   ```
3. Pull and list an image with CRI:
   ```bash
   sudo crictl pull alpine:3.20
   sudo crictl images | grep alpine
   ```
4. Compare process/runtime visibility:
   ```bash
   docker ps -a
   sudo crictl ps -a
   ```
5. Capture your mapping notes:
   - Docker image list command -> CRI equivalent
   - Docker container list command -> CRI equivalent
   - Primary runtime service name on node

## Verify
- You can list images using both Docker and `crictl`.
- You can list containers/sandboxes using `crictl`.
- You documented at least three Docker-to-CRI command mappings.

## Cleanup
- `docker rmi alpine:3.20 || true`
- `sudo crictl rmi alpine:3.20 || true`

## Next
Use this mapping in every Kubernetes incident runbook.

## Concept Check
- Why can `docker ps` be empty while Kubernetes workloads are still running?
- What command tells you runtime truth on a kubelet-managed node?
- What migration risk appears if SREs only know Docker CLI?

## Why This Lab Proves Understanding
- Verify confirms you can operate and debug at the runtime layer Kubernetes actually uses.
- Cleanup confirms you can leave the node in a known-safe state.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] You can list images using both Docker and `crictl`.
- [ ] You can list containers/sandboxes using `crictl`.
- [ ] You documented at least three Docker-to-CRI command mappings.
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Output differs materially from expected behavior.
- Environment not in clean state after cleanup.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
