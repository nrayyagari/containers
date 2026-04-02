# Networking

## Context & Problem
Container networking failures are usually Linux networking failures with container-specific defaults layered on top. Teams lose time when they debug the app first instead of proving the packet path, namespace path, DNS path, and policy path.

## First Principles
A container network is still made of interfaces, namespaces, routes, bridges, NAT, sockets, and DNS. The platform adds convenience, but the kernel still decides how traffic moves.

## Production Implementation
Treat every network symptom as a path problem: where does name resolution happen, where does the packet enter, where is it translated, and where is it dropped? Until that path is explicit, the root cause is still guesswork.

## Troubleshooting Approach
Use direct evidence from `ip`, `ss`, routing tables, bridge state, NAT rules, and packet capture before changing service configs. Connectivity problems often look application-level until you inspect the host.

## Evolution & Alternatives
Container networking grew from simple bridges and host port publishing into overlay networks, service discovery, and policy-heavy orchestration environments. The abstractions changed, but packet mechanics did not.

## How To Use This Module
1. Read the topic README before touching the commands or the runtime.
2. Write down the boundary each topic controls and one failure mode that boundary can create.
3. If a lab exists, finish it only when you can explain the output from first principles and identify the first diagnostic action you would take in production.

## Topic Map
- [01-bridge-networking](./01-bridge-networking/README.md): how the default bridge model connects containers through a Linux bridge and NAT.
- [02-host-networking](./02-host-networking/README.md): what happens when a container shares the host network stack.
- [03-overlay-networking](./03-overlay-networking/README.md): how overlay networks span hosts and carry container traffic through encapsulation.
- [04-macvlan-ipvlan](./04-macvlan-ipvlan/README.md): how containers get more direct Layer 2 or Layer 3 identity on the physical network.
- [05-dns-service-discovery](./05-dns-service-discovery/README.md): how containers resolve service names and where DNS failures usually hide.
- [06-port-mapping](./06-port-mapping/README.md): how published ports expose container listeners on host addresses.
- [07-network-namespaces](./07-network-namespaces/README.md): how the kernel isolates interfaces, routes, and sockets per container.
- [08-docker-proxy](./08-docker-proxy/README.md): what docker-proxy does and when kernel NAT can replace it.
- [09-iptables-rules](./09-iptables-rules/README.md): how packet filtering and NAT rules implement container connectivity.
- [10-ipv6](./10-ipv6/README.md): what changes when containers participate in IPv6 networks.

## Completion Standard
- You can explain the mechanism in plain language without hiding behind tool names.
- You can point to the signal that proves the mechanism is working or failing.
- You know which first diagnostic step is justified when this topic breaks in production.

## Next Steps
After networking, move to storage and security so you can reason about the other two boundaries most likely to fail under pressure: state and privilege.
Continue with [Storage](../06-storage/README.md) when the topic map in this module feels operationally clear.
