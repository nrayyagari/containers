# Service Mesh Lab

## Goal
Build practical intuition for service-mesh value and cost using a focused test scenario.

## Prerequisites
- `kubectl` connected to test cluster
- Optional: Istio or Linkerd test environment

## Steps
1. Pick one service-to-service flow in your app (A -> B).
2. Document current controls without mesh:
   - Encryption status
   - Retry/timeouts location
   - Authorization enforcement point
3. (If mesh available) enable namespace injection and deploy sample app.
4. Apply one traffic policy (for example retry or timeout) and one security policy (for example mTLS strict mode).
5. Observe behavior before/after policy with simple request tests and pod logs.

## Verify
- You can describe one control that became easier with mesh.
- You can describe one operational overhead mesh introduces.
- If tooling is available, policy effect is observable in request behavior or logs.

## Cleanup
- Remove sample resources and disable injection in test namespace.
- Confirm test namespace is back to baseline.

## Next
Adopt mesh first in high-value, high-risk service boundaries.

## Concept Check
- What problem does mesh solve better than app-library-only approaches?
- When does mesh complexity exceed its benefit?
- Which metric should decide if mesh rollout is helping or hurting?

## Why This Lab Proves Understanding
- Verify forces balanced evaluation of both capability gain and operational cost.
- Cleanup confirms controlled experimentation practice.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] You can describe one control that became easier with mesh.
- [ ] You can describe one operational overhead mesh introduces.
- [ ] If tooling is available, policy effect is observable in request behavior or logs.
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Trade-off analysis is superficial or incorrect.
- Environment not in clean state after cleanup.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
