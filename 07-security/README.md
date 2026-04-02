# Security

## Context & Problem
Container security is often oversimplified into image scanning or a single runtime flag. Real security comes from reducing blast radius at several layers: identity, filesystem access, kernel attack surface, image trust, and runtime detection.

## First Principles
A secure container is not one magical setting. It is the result of using the smallest necessary privileges, shipping a smaller and more trustworthy artifact, and keeping enough runtime visibility to detect abuse after the process starts.

## Production Implementation
Treat security as a series of layered decisions: who the process runs as, which capabilities it keeps, which syscalls it can make, which files it can access, which image is allowed to run, and what you will do if it misbehaves anyway.

## Troubleshooting Approach
Security controls can break workloads in subtle ways. When something fails, identify whether the block is caused by user mapping, capability removal, seccomp, AppArmor, SELinux, registry policy, or runtime detection before loosening everything at once.

## Evolution & Alternatives
Container security matured from 'don't run privileged' into supply-chain verification, rootless modes, stronger policy enforcement, and runtime threat detection. The deeper lesson is that no single layer is sufficient by itself.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-user-namespace-mapping](./01-user-namespace-mapping/README.md): how container UIDs and GIDs map to less-privileged host IDs.
- [02-rootless-containers](./02-rootless-containers/README.md): how to run containers without a privileged daemon or root-owned workloads.
- [03-drop-capabilities](./03-drop-capabilities/README.md): how to remove unnecessary Linux capabilities from a container.
- [04-seccomp-profiles](./04-seccomp-profiles/README.md): how seccomp profiles control the syscalls a process may use.
- [05-apparmor-profiles](./05-apparmor-profiles/README.md): how AppArmor policies constrain file, network, and capability access.
- [06-selinux](./06-selinux/README.md): how SELinux labels enforce mandatory separation beyond classic Unix permissions.
- [07-image-scanning](./07-image-scanning/README.md): how vulnerability scanners inspect image contents and package metadata.
- [08-trivy-snyk](./08-trivy-snyk/README.md): how common image scanners differ in workflow, data sources, and trade-offs.
- [09-image-signing](./09-image-signing/README.md): how signatures and attestations prove image origin and integrity.
- [10-privileged-containers](./10-privileged-containers/README.md): what privileged mode actually grants and why it is dangerous.
- [11-security-best-practices](./11-security-best-practices/README.md): how to combine build-time, runtime, and registry controls into defense in depth.
- [12-runtime-security](./12-runtime-security/README.md): how to detect and contain malicious or unexpected behavior after a container starts.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After security, registry and orchestration topics become easier because you will understand how trust and policy travel with the artifact into runtime environments.
Continue with [Registry](../08-registry/README.md) when the topic map in this module feels operationally clear.
