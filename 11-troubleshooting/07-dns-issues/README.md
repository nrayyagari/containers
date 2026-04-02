# Dns Issues

## What It Is
Dns Issues covers How resolver config and upstream failures affect container lookups.

## Why It Matters
It matters because fast recovery depends on asking the next correct question.

## Key Points
- Container networking is still interfaces, routes, sockets, NAT, and DNS underneath.
- Name resolution, forwarding, and policy are separate hops in the path.
- A network issue is not understood until you can describe where the next packet should go.

## Practice Check
- Start with the least disruptive signal available.
- Build a short timeline before you touch restart or cleanup commands.

## Common Mistakes
- Changing app config before proving the packet path.
- Treating DNS, routing, and firewall behavior as one problem.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Exit Codes](../08-exit-codes/README.md).
