# Push and Pull Lab

## Goal
Develop hands-on confidence for Push and Pull and prove understanding through observable output.

## Prerequisites
- Docker Engine with permission to run a disposable registry container.
- If your engine does not allow plain HTTP to `localhost` by default, configure local insecure-registry access for the lab port.
- Permission to run commands for this module.

## Steps
1. Start a local registry dedicated to the push/pull workflow.
   COMMAND: docker run -d -p 5002:5000 --name push-reg registry:3
2. Push an image into the registry.
   COMMAND: docker pull busybox:1.36
   COMMAND: docker tag busybox:1.36 localhost:5002/push-lab:1
   COMMAND: docker push localhost:5002/push-lab:1
3. Record the pushed digest, remove the local copy, and pull it back.
   COMMAND: docker image inspect localhost:5002/push-lab:1 --format "{{index .RepoDigests 0}}"
   COMMAND: docker image rm localhost:5002/push-lab:1
   COMMAND: docker pull localhost:5002/push-lab:1
4. Inspect registry logs and explain which objects were uploaded or reused by digest.
   COMMAND: docker logs push-reg | tail -n 30

## Expected Observations
- Command output contains concrete evidence for this topic.
- You can point to at least one line that proves the artifact identity, access control, or registry behavior.
- You can relate the observed behavior to one production failure mode.

## Verify
- All steps executed without unresolved errors.
- You can explain the behavior from first principles.
- You identified one failure mode and the first diagnostic action.

## Cleanup
- Remove the push/pull lab registry: docker rm -f push-reg 2>/dev/null || true

## Concept Check
- Which output proves the pull operation is content-addressed underneath even when you requested a tag?
- Why does digest reuse make repeated pulls cheaper than re-uploading identical content?
- What troubleshooting signal would you inspect first if pushes succeed locally but other hosts cannot pull the artifact?

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
