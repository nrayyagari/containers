# Cri Compatibility Lab

## Goal
Validate that CRI endpoint configuration is correct for node runtime communication.

## Prerequisites
- Linux host with kubelet and containerd.
- crictl installed.

## Steps
1. Inspect crictl endpoint config.
   COMMAND: cat /etc/crictl.yaml 2>/dev/null || echo "crictl config missing"
2. Check runtime connectivity.
   COMMAND: crictl info || true
3. Inspect kubelet runtime endpoint arguments.
   COMMAND: ps -ef | grep kubelet | grep -E 'container-runtime-endpoint|cri' || true
4. Scan kubelet logs for CRI errors.
   COMMAND: journalctl -u kubelet --no-pager | grep -Ei 'runtime|cri|socket|containerd' | tail -n 30

## Expected Observations
- You can identify configured runtime endpoint socket.
- crictl info succeeds or returns actionable endpoint error.
- kubelet logs reveal if endpoint mismatch exists.

## Verify
- Runtime endpoint path is explicitly identified.
- crictl and kubelet endpoint settings are consistent.
- No unresolved CRI socket errors remain after validation.

## Cleanup
- No cleanup required.

## Concept Check
- Which endpoint mismatch would cause kubelet-runtime communication failure?
- Which log signal confirms CRI recovery after fixing endpoint config?
- What preflight check should be mandatory for every new node?

## Why This Lab Proves Understanding
- You validated endpoint correctness with both config and runtime evidence.

## Answer Key
Pass when all Verify points are satisfied.
