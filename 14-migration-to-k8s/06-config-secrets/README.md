# Config and Secrets

## What It Is
Config and Secrets covers How Kubernetes separates config and secret delivery from the image.

## Why It Matters
It matters because Kubernetes migration fails when Docker assumptions are copied over unchanged.

## Key Points
- Container security is layered; no single flag makes a workload safe.
- Least privilege means reducing what the process can do and what you trust it with.
- A security control is only useful if you can explain what it blocks.

## Lab Focus
Use the lab to prove how Kubernetes separates config and secret delivery from the image.
- Key commands:
  - `kubectl create configmap app-config --from-literal=APP_MODE=staging`
  - `kubectl create secret generic app-secret --from-literal=DB_PASSWORD=demo-pass`
  - `kubectl run config-check --image=alpine:3.20 --restart=Never --env-from=configmap/app-config --env-from=secret/app-secret --command -- sh -c 'sleep 300'`
- Finish only when:
  - Config value resolved in pod.
  - Secret value resolved in pod.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Networking Changes](../07-networking-changes/README.md).
