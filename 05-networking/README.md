# Networking

## What This Module Covers
This module explains container networking as Linux networking plus platform defaults. It covers bridges, namespaces, DNS, port publishing, overlays, packet filtering, and IPv6.

## How To Study It
1. Read the topic README first.
2. Write one sentence for what the topic is and one sentence for what can fail.
3. If a lab exists, do not move on until you can explain the proof signal.

## Topic Map
- [01-bridge-networking](./01-bridge-networking/README.md) | [Lab](./01-bridge-networking/LAB.md): how the default bridge model connects containers through a Linux bridge and NAT.
- [02-host-networking](./02-host-networking/README.md) | [Lab](./02-host-networking/LAB.md): what changes when a container shares the host network stack.
- [03-overlay-networking](./03-overlay-networking/README.md) | [Lab](./03-overlay-networking/LAB.md): how overlay networks carry container traffic across hosts.
- [04-macvlan-ipvlan](./04-macvlan-ipvlan/README.md) | [Lab](./04-macvlan-ipvlan/LAB.md): how containers get more direct network identity on the physical network.
- [05-dns-service-discovery](./05-dns-service-discovery/README.md) | [Lab](./05-dns-service-discovery/LAB.md): how containers resolve service names and where DNS failures hide.
- [06-port-mapping](./06-port-mapping/README.md) | [Lab](./06-port-mapping/LAB.md): how published ports expose container listeners on host addresses.
- [07-network-namespaces](./07-network-namespaces/README.md) | [Lab](./07-network-namespaces/LAB.md): how the kernel isolates interfaces, routes, and sockets per container.
- [08-docker-proxy](./08-docker-proxy/README.md) | [Lab](./08-docker-proxy/LAB.md): what docker-proxy does and when kernel NAT can replace it.
- [09-iptables-rules](./09-iptables-rules/README.md) | [Lab](./09-iptables-rules/LAB.md): how iptables implements forwarding and NAT for containers.
- [10-ipv6](./10-ipv6/README.md) | [Lab](./10-ipv6/LAB.md): what changes when containers participate in IPv6 networks.

## Move On When
- You can meet this module's main goal: Be able to describe the packet path before changing network config.
- You can name the first signal you would check during an incident in this area.
- You no longer need the topic names to explain the mechanism.

## Next
Continue with [Storage](../06-storage/README.md).
