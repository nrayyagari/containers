# IPv6

## What It Is
IPv6 covers What changes when containers participate in IPv6 networks.

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
Then continue to [Storage](../../06-storage/README.md).
