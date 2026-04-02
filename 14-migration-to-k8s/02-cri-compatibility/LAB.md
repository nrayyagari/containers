# CRI Compatibility Lab

## Goal
Validate that kubelet and `crictl` point to a working CRI runtime endpoint.

## Prerequisites
- Linux host with containerd and `crictl`
- Access to kubelet config/logs (recommended)

## Steps
1. Check `crictl` endpoint config:
   ```bash
   sudo cat /etc/crictl.yaml || true
   ```
2. Query runtime info:
   ```bash
   sudo crictl info
   ```
3. List pods and containers from runtime:
   ```bash
   sudo crictl pods
   sudo crictl ps -a
   ```
4. Verify kubelet runtime endpoint setting:
   ```bash
   ps -ef | grep kubelet | grep -E 'container-runtime-endpoint|cri' || true
   ```
5. Correlate with kubelet logs for CRI errors:
   ```bash
   sudo journalctl -u kubelet --no-pager | grep -Ei 'runtime|cri|containerd|socket' | tail -n 30
   ```

## Verify
- `crictl info` succeeds without endpoint errors.
- Runtime endpoint used by kubelet matches expected socket.
- No unresolved CRI socket/version errors in recent kubelet logs.

## Cleanup
- No cleanup needed.

## Next
Bake CRI endpoint validation into node bootstrap checks.

## Concept Check
- Which two signals confirm CRI endpoint health beyond "service is running"?
- Why must kubelet and `crictl` target the same socket during incident debugging?
- What happens to pod scheduling if CRI connectivity degrades intermittently?

## Why This Lab Proves Understanding
- Verify checks endpoint correctness and observable kubelet/runtime alignment.
- No-cleanup lab still requires evidence capture for operational rigor.

## Answer Key
A lab is considered successful only when every Verify condition is true.

Pass criteria (all required):
- [ ] `crictl info` succeeds without endpoint errors.
- [ ] Runtime endpoint used by kubelet matches expected socket.
- [ ] No unresolved CRI socket/version errors in recent kubelet logs.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- CRI communication errors remain unresolved.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
