# Macvlan Ipvlan

## What It Is
Macvlan Ipvlan covers How containers get more direct network identity on the physical network.

## Why It Matters
It matters because most container network incidents are path problems hidden by abstraction.

## Key Points
- macvlan and ipvlan give containers a more direct network identity than bridge mode.
- That can simplify some integrations but increases dependence on host and physical-network behavior.
- The trade-off is usually less abstraction and more operational responsibility.

## Practice Check
- Draw the traffic path before changing anything.
- Use `ip`, `ss`, `docker network inspect`, or packet capture to prove where the path breaks.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [DNS and Service Discovery](../05-dns-service-discovery/README.md).
