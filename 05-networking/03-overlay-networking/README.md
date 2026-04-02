# Overlay Networking

## What It Is
Overlay Networking covers How overlay networks carry container traffic across hosts.

## Why It Matters
It matters because most container network incidents are path problems hidden by abstraction.

## Key Points
- Image layers, writable layers, and persistent volumes have different lifecycles.
- Copy-on-write behavior affects both performance and troubleshooting.
- Durability depends on where data is stored, not on whether the write succeeded once.

## Practice Check
- Draw the traffic path before changing anything.
- Use `ip`, `ss`, `docker network inspect`, or packet capture to prove where the path breaks.

## Common Mistakes
- Changing app config before proving the packet path.
- Treating DNS, routing, and firewall behavior as one problem.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Macvlan Ipvlan](../04-macvlan-ipvlan/README.md).
