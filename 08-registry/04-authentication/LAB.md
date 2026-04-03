# Authentication Lab

## Goal
Develop hands-on confidence for Authentication and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to run disposable helper containers.
- If your engine does not allow plain HTTP to `localhost` by default, configure local insecure-registry access for the lab port.
- Permission to run commands for this module.

## Steps
1. Generate an `htpasswd` file for the registry.
   COMMAND: rm -rf /tmp/auth-reg
   COMMAND: mkdir -p /tmp/auth-reg/auth
   COMMAND: docker run --rm --entrypoint htpasswd httpd:2 -Bbn labuser labpass > /tmp/auth-reg/auth/htpasswd
2. Start a registry that requires basic authentication.
   COMMAND: docker run -d --name auth-reg -p 5001:5000 -v /tmp/auth-reg/auth:/auth -e REGISTRY_AUTH=htpasswd -e REGISTRY_AUTH_HTPASSWD_REALM="Registry Realm" -e REGISTRY_AUTH_HTPASSWD_PATH=/auth/htpasswd registry:3
3. Prove unauthenticated access is rejected, then log in successfully.
   COMMAND: curl -I http://localhost:5001/v2/ || true
   COMMAND: printf 'labpass\n' | docker login localhost:5001 -u labuser --password-stdin
4. Repeat the API call with credentials and confirm access succeeds.
   COMMAND: curl -su labuser:labpass http://localhost:5001/v2/

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove authentication lab resources: docker rm -f auth-reg 2>/dev/null || true; rm -rf /tmp/auth-reg

## Concept Check
- Which response proves the registry is enforcing authentication rather than merely hiding data in the UI?
- Why is authentication distinct from authorization in a registry workflow?
- What is the first thing you should inspect when pulls fail only for certain users or automation accounts?

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
