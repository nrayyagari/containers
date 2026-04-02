# User Namespace Mapping

## Context & Problem
This topic explains how container UIDs and GIDs map to less-privileged host IDs. In production, this matters because container security fails when teams treat one control as sufficient instead of layering identity, policy, and trust.
A namespace is not a whole container by itself; it is one scoped view of one class of system resources.

## First Principles
- Namespaces change what a process can see, not what the host physically contains.
- Different namespace types isolate different resources: PID, network, mount, IPC, UTS, and user IDs.
- A convincing container boundary appears only when namespaces are combined with cgroups, a filesystem, and security policy.

## Production Implementation
Treat this control as one layer in a defense-in-depth model. Production hardening means preserving just enough privilege for the workload to function and then proving that the control you added is actually enforced.

## Troubleshooting Approach
When isolation looks wrong, compare namespace links under `/proc/<pid>/ns` and decide which namespace is actually shared. Do not start with firewall or filesystem changes until you know the scope is correct.

## Evolution & Alternatives
Container security shifted from 'don't run everything as root' into a broader supply-chain and runtime-hardening discipline. The deeper improvement was treating trust as an end-to-end property rather than a runtime-only property.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Practice on a disposable workload or host so you can observe before-and-after behavior without cleanup risk.
- Capture one direct signal that proves the mechanism and one failure mode that would invalidate your assumption.
- Explain the topic back in plain language before moving on.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Rootless Containers](../02-rootless-containers/README.md).
