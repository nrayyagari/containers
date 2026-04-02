# DNS and Service Discovery

## Context & Problem
This topic explains how containers resolve service names and where DNS failures usually hide. In production, this matters because most container network incidents are really packet-path or name-resolution problems hidden by abstraction.

## First Principles
- Container networking is still Linux networking: interfaces, routes, sockets, bridges, NAT, and packet filters.
- Name resolution, traffic forwarding, and policy enforcement are different hops in the path and can fail independently.
- You do not really understand a network issue until you can describe where the packet should go next.

## Production Implementation
Draw the traffic path before changing any configuration. In practice that means checking namespace layout, interface attachment, routes, name resolution, and NAT or policy translation one hop at a time.

## Troubleshooting Approach
Start by proving where the path breaks: name resolution, route selection, listener binding, translation, or policy. Packet capture or explicit socket inspection is often the fastest way to stop guessing.

## Evolution & Alternatives
Network abstractions evolved from one-host bridges to multi-host overlays and service meshes. The abstractions changed mainly to address scale, mobility, and policy, not to replace basic packet mechanics.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Inspect topology first with `docker network inspect`, `ip addr`, `ip route`, or the equivalent host tools.
- Use `ss`, `curl`, or packet capture to prove whether the listener, path, and response all match your expectation.
- Change one network variable at a time and validate where the packet path changed.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Port Mapping](../06-port-mapping/README.md).
