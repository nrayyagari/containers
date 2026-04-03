# Registry API Lab

## Goal
Develop hands-on confidence for Registry API and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to run a disposable registry container.
- If your engine does not allow plain HTTP to `localhost` by default, configure local insecure-registry access for the lab port.
- `jq` available for response inspection.
- Permission to run commands for this module.

## Steps
1. Start a local registry and push a sample image.
   COMMAND: docker run -d --name api-reg -p 5005:5000 registry:3
   COMMAND: docker pull busybox:1.36
   COMMAND: docker tag busybox:1.36 localhost:5005/api-lab:1
   COMMAND: docker push localhost:5005/api-lab:1
2. Check the base API endpoint.
   COMMAND: curl -i http://localhost:5005/v2/
3. List tags and fetch the manifest JSON.
   COMMAND: curl -s http://localhost:5005/v2/api-lab/tags/list | jq
   COMMAND: curl -s -H "Accept: application/vnd.docker.distribution.manifest.v2+json" http://localhost:5005/v2/api-lab/manifests/1 | jq ".schemaVersion, .mediaType"
4. Explain which endpoint and header values uniquely identify the object you retrieved.

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the registry API lab container: docker rm -f api-reg 2>/dev/null || true

## Concept Check
- Which response proves you are interacting with a standard distribution API rather than only with Docker CLI abstractions?
- Why does the `Accept` header matter when working with manifests programmatically?
- What automation task becomes easier once you understand the registry API directly?

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
