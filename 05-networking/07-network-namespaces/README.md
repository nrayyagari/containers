# Network Namespaces

## What It Is
Network Namespaces covers How the kernel isolates interfaces, routes, and sockets per container.

## Why It Matters
It matters because most container network incidents are path problems hidden by abstraction.

## Key Points
- Each namespace type isolates one category of resources, not everything.
- PID and network namespaces are usually the easiest places to prove isolation.
- Namespaces alone are not a complete container boundary; cgroups and security controls still matter.

## Practice Check
- Draw the traffic path before changing anything.
- Use `ip`, `ss`, `docker network inspect`, or packet capture to prove where the path breaks.

## Common Mistakes
- Changing app config before proving the packet path.
- Treating DNS, routing, and firewall behavior as one problem.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Docker Proxy](../08-docker-proxy/README.md).
