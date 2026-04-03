# Artifact Management Lab

## Goal
Develop hands-on confidence for Artifact Management and prove understanding through observable output.

## Prerequisites
- ORAS installed and permission to run a disposable registry container.
- Registry and ORAS access available over plain HTTP on `localhost` for the lab.
- Permission to run commands for this module.

## Steps
1. Start a local registry and prepare a non-image artifact.
   COMMAND: docker run -d --name artifact-reg -p 5006:5000 registry:3
   COMMAND: rm -rf /tmp/artifact-lab
   COMMAND: mkdir -p /tmp/artifact-lab
   COMMAND: printf '%s\n' '{"sbom":"demo"}' > /tmp/artifact-lab/sbom.json
2. Push the artifact with ORAS.
   COMMAND: oras push --plain-http --artifact-type application/spdx+json localhost:5006/artifact-lab:v1 /tmp/artifact-lab/sbom.json:application/spdx+json
3. Fetch the stored manifest and list repository tags.
   COMMAND: oras manifest fetch --plain-http localhost:5006/artifact-lab:v1
   COMMAND: oras repo tags --plain-http localhost:5006/artifact-lab
4. Explain how this differs from storing a runnable image and where OCI artifacts fit in the supply chain.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove artifact-management lab resources: docker rm -f artifact-reg 2>/dev/null || true; rm -rf /tmp/artifact-lab

## Concept Check
- Which output proves the registry can store OCI artifacts that are not container root filesystems?
- Why does artifact support matter for SBOMs, attestations, and other supply-chain metadata?
- What operational advantage comes from keeping related artifacts in the same registry namespace as the image they describe?

## Why This Lab Proves Understanding
- It validates execution, interpretation, and operational cleanup.

## Answer Key
A lab is successful only when every Verify condition is true and cleanup is complete.

Pass criteria (all required):
- [ ] Steps completed and expected observations captured.
- [ ] Behavior explanation is accurate and mechanism-based.
- [ ] Failure mode and first diagnostic action documented.
- [ ] Cleanup completed with no leftover lab artifacts.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Output interpretation is unclear or incorrect.
- Environment is not clean after cleanup.
