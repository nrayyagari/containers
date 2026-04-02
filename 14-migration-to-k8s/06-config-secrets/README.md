# Config and Secrets

## Context & Problem
This topic explains how Kubernetes separates configuration and secret delivery from the image. In production, this matters because a Kubernetes migration fails when Docker concepts are translated literally instead of rethought.

## First Principles
- Security controls are layered; no single flag makes a workload safe.
- Least privilege means reducing both what the process is allowed to do and how much trust you place in the artifact it runs from.
- A control is only useful if you can explain what it blocks and how you will verify that block during troubleshooting.

## Production Implementation
Use this topic to challenge a Docker-era assumption directly. In migration work, the risk is not ignorance of YAML; it is keeping the old mental model after the platform boundary has changed.

## Troubleshooting Approach
If the workload fails after hardening, identify the blocking layer before loosening everything. Security debugging is safe only when you can say whether identity, policy, syscall filtering, or trust verification caused the failure.

## Evolution & Alternatives
Migration thinking changed after dockershim removal and the rise of CRI-native nodes. The successful path now is to adopt Kubernetes-native operating concepts rather than preserve Docker-era habits behind new YAML.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `kubectl create configmap app-config --from-literal=APP_MODE=staging`
- `kubectl create secret generic app-secret --from-literal=DB_PASSWORD=demo-pass`
- `kubectl run config-check --image=alpine:3.20 --restart=Never --env-from=configmap/app-config --env-from=secret/app-secret --command -- sh -c 'sleep 300'`
- `kubectl exec config-check -- printenv | grep APP_MODE`

### What Success Looks Like
- Config value resolved in pod.
- Secret value resolved in pod.
- Rotation rationale documented.

### Questions To Answer After The Lab
- Which output proves config and secret separation is correctly implemented?
- What security incident risk appears if secrets are image-baked or log-exposed?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Networking Changes](../07-networking-changes/README.md).
