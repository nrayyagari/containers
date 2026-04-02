# Network Namespaces

## Context & Problem
This topic explains how the kernel isolates interfaces, routes, and sockets per container. In production, this matters because most container network incidents are really packet-path or name-resolution problems hidden by abstraction.
A namespace is not a whole container by itself; it is one scoped view of one class of system resources.

## First Principles
- Namespaces change what a process can see, not what the host physically contains.
- Different namespace types isolate different resources: PID, network, mount, IPC, UTS, and user IDs.
- A convincing container boundary appears only when namespaces are combined with cgroups, a filesystem, and security policy.

## Production Implementation
Draw the traffic path before changing any configuration. In practice that means checking namespace layout, interface attachment, routes, name resolution, and NAT or policy translation one hop at a time.

## Troubleshooting Approach
When isolation looks wrong, compare namespace links under `/proc/<pid>/ns` and decide which namespace is actually shared. Do not start with firewall or filesystem changes until you know the scope is correct.

## Evolution & Alternatives
Network abstractions evolved from one-host bridges to multi-host overlays and service meshes. The abstractions changed mainly to address scale, mobility, and policy, not to replace basic packet mechanics.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Inspect topology first with `docker network inspect`, `ip addr`, `ip route`, or the equivalent host tools.
- Use `ss`, `curl`, or packet capture to prove whether the listener, path, and response all match your expectation.
- Change one network variable at a time and validate where the packet path changed.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Docker Proxy](../08-docker-proxy/README.md).
