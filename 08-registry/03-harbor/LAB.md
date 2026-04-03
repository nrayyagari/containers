# Harbor Lab

## Goal
Develop hands-on confidence for Harbor and prove understanding through observable output.

## Prerequisites
- A Harbor instance, a project you can push to, and credentials with API access.
- `jq` available for inspecting Harbor API responses; self-signed TLS may require `curl -k` in lab environments.
- Permission to run commands for this module.

## Steps
1. Export the Harbor endpoint and project information.
   COMMAND: export HARBOR_URL=harbor.example.com
   COMMAND: export HARBOR_PROJECT=library
2. Log in and list visible projects through the Harbor API.
   COMMAND: docker login ${HARBOR_URL}
   COMMAND: curl -sk -u "${HARBOR_USER}:${HARBOR_PASS}" "https://${HARBOR_URL}/api/v2.0/projects" | jq '.[].name'
3. Push a test image into the Harbor project.
   COMMAND: docker pull alpine:3.20
   COMMAND: docker tag alpine:3.20 ${HARBOR_URL}/${HARBOR_PROJECT}/harbor-lab:1
   COMMAND: docker push ${HARBOR_URL}/${HARBOR_PROJECT}/harbor-lab:1
4. Record the pushed digest and identify one Harbor control that would apply to this artifact.
   COMMAND: docker image inspect ${HARBOR_URL}/${HARBOR_PROJECT}/harbor-lab:1 --format "{{index .RepoDigests 0}}"

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Optionally log out after the lab: docker logout ${HARBOR_URL} 2>/dev/null || true

## Concept Check
- Which output proves Harbor is storing the artifact by digest, not by UI presentation alone?
- What additional operational controls does Harbor provide beyond a plain OCI distribution registry?
- Why is project-level governance as important as simple image storage in regulated or multi-team environments?

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
