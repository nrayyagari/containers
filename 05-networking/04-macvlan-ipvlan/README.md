# Macvlan Ipvlan

## Context & Problem
This topic explains how containers get more direct Layer 2 or Layer 3 identity on the physical network. In production, this matters because most container network incidents are really packet-path or name-resolution problems hidden by abstraction.

## First Principles
- macvlan and ipvlan reduce the abstraction between a container and the physical network.
- They are useful when you need more direct network identity than a bridge typically provides.
- The trade-off is operational complexity: the physical network, upstream switching, and host routing assumptions matter more.

## Production Implementation
Draw the traffic path before changing any configuration. In practice that means checking namespace layout, interface attachment, routes, name resolution, and NAT or policy translation one hop at a time.

## Troubleshooting Approach
Start with direct evidence at the layer this topic controls, then expand outward only if the observed state matches expectations.

## Evolution & Alternatives
Network abstractions evolved from one-host bridges to multi-host overlays and service meshes. The abstractions changed mainly to address scale, mobility, and policy, not to replace basic packet mechanics.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Practice on a disposable workload or host so you can observe before-and-after behavior without cleanup risk.
- Capture one direct signal that proves the mechanism and one failure mode that would invalidate your assumption.
- Explain the topic back in plain language before moving on.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [DNS and Service Discovery](../05-dns-service-discovery/README.md).
