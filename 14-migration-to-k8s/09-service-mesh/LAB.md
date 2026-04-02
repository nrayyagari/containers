# Service Mesh Lab

## Goal
Assess when service mesh adds value and when it adds unnecessary complexity.

## Prerequisites
- kubectl access to test cluster.
- Optional mesh installation (Istio or Linkerd) for live validation.

## Steps
1. Select one service-to-service flow (A to B).
2. Document current controls without mesh:
   - transport encryption
   - retries/timeouts
   - authorization policy location
3. If mesh is available, apply one traffic policy and one security policy to this flow.
4. Measure before/after behavior and record operational overhead.

## Expected Observations
- You identify at least one control simplified by mesh.
- You identify at least one operational overhead introduced by mesh.
- If tooling exists, policy effect is observable in logs/requests.

## Verify
- Benefit and cost are both documented with concrete evidence.
- You defined one criterion for adopting mesh and one for deferring it.
- You mapped one failure mode to mesh-vs-app diagnostic path.

## Cleanup
- Remove test mesh resources and disable test injection settings.

## Concept Check
- Which specific control became easier with mesh in your tested flow?
- What operational overhead did you observe that must be budgeted?
- Which KPI should decide whether to continue or pause mesh rollout?

## Why This Lab Proves Understanding
- You performed balanced trade-off analysis, not one-sided adoption.

## Answer Key
Pass when all Verify points are satisfied and cleanup is complete.
