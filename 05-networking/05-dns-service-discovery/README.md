# DNS and Service Discovery

## What It Is
DNS and Service Discovery covers How containers resolve service names and where DNS failures hide.

## Why It Matters
It matters because most container network incidents are path problems hidden by abstraction.

## Key Points
- Container networking is still interfaces, routes, sockets, NAT, and DNS underneath.
- Name resolution, forwarding, and policy are separate hops in the path.
- A network issue is not understood until you can describe where the next packet should go.

## Practice Check
- Draw the traffic path before changing anything.
- Use `ip`, `ss`, `docker network inspect`, or packet capture to prove where the path breaks.

## Common Mistakes
- Changing app config before proving the packet path.
- Treating DNS, routing, and firewall behavior as one problem.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Port Mapping](../06-port-mapping/README.md).
