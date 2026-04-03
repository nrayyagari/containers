# Garbage Collection Lab

## Goal
Develop hands-on confidence for Garbage Collection and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to run a disposable registry and execute commands inside it.
- If your engine does not allow plain HTTP to `localhost` by default, configure local insecure-registry access for the lab port.
- Permission to run commands for this module.

## Steps
1. Create a registry configuration that enables deletes.
   COMMAND: rm -rf /tmp/gc-reg
   COMMAND: mkdir -p /tmp/gc-reg
   COMMAND: printf '%s\n' 'version: 0.1' 'storage:' '  filesystem:' '    rootdirectory: /var/lib/registry' 'delete:' '  enabled: true' > /tmp/gc-reg/config.yml
2. Start the registry and push a test image.
   COMMAND: docker run -d --name gc-reg -p 5004:5000 -v /tmp/gc-reg/config.yml:/etc/distribution/config.yml registry:3
   COMMAND: docker pull busybox:1.36
   COMMAND: docker tag busybox:1.36 localhost:5004/gc-lab:1
   COMMAND: docker push localhost:5004/gc-lab:1
3. Resolve the manifest digest and delete the manifest reference.
   COMMAND: DIGEST=$(curl -sI -H 'Accept: application/vnd.docker.distribution.manifest.v2+json' http://localhost:5004/v2/gc-lab/manifests/1 | awk -F': ' '/Docker-Content-Digest/ {print $2}' | tr -d '\r')
   COMMAND: echo "${DIGEST}"
   COMMAND: curl -X DELETE http://localhost:5004/v2/gc-lab/manifests/${DIGEST}
4. Run registry garbage collection and inspect remaining storage.
   COMMAND: docker exec gc-reg registry garbage-collect /etc/distribution/config.yml
   COMMAND: docker exec gc-reg du -sh /var/lib/registry

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove garbage-collection lab resources: docker rm -f gc-reg 2>/dev/null || true; rm -rf /tmp/gc-reg

## Concept Check
- Which step proves deleting a manifest reference is not the same as reclaiming blob storage immediately?
- Why is offline or carefully coordinated garbage collection important on busy registries?
- What risk appears if operators assume tag deletion instantly frees space?

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
