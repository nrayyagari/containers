# Security

## What This Module Covers
This module covers the security layers around a container: user mapping, rootless mode, capabilities, syscall filtering, MAC policy, image scanning, signing, and runtime protection.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-user-namespace-mapping](./01-user-namespace-mapping/README.md): how container IDs map to less-privileged host IDs.
- [02-rootless-containers](./02-rootless-containers/README.md): how to run containers without a privileged daemon or root-owned process.
- [03-drop-capabilities](./03-drop-capabilities/README.md): how to remove unnecessary Linux capabilities.
- [04-seccomp-profiles](./04-seccomp-profiles/README.md): how seccomp limits which syscalls a process may use.
- [05-apparmor-profiles](./05-apparmor-profiles/README.md): how AppArmor constrains file, network, and capability access.
- [06-selinux](./06-selinux/README.md): how SELinux labels enforce mandatory separation.
- [07-image-scanning](./07-image-scanning/README.md): how scanners inspect images for known vulnerabilities.
- [08-trivy-snyk](./08-trivy-snyk/README.md): how common image scanners differ in workflow and findings.
- [09-image-signing](./09-image-signing/README.md): how signatures and attestations prove image origin and integrity.
- [10-privileged-containers](./10-privileged-containers/README.md): what privileged mode really grants and why it is dangerous.
- [11-security-best-practices](./11-security-best-practices/README.md): how to combine build-time and runtime controls into defense in depth.
- [12-runtime-security](./12-runtime-security/README.md): how to detect and contain suspicious behavior after startup.

## Move On When
- You can meet this module's main goal: Reduce privilege and improve trust without breaking the workload blindly.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Registry](../08-registry/README.md).
