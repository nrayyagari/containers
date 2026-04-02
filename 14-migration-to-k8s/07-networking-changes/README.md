# Networking Changes

## What It Is
Networking Changes covers How service exposure, DNS, and network policy change in Kubernetes.

## Why It Matters
It matters because Kubernetes migration fails when Docker assumptions are copied over unchanged.

## Key Points
- Container networking is still interfaces, routes, sockets, NAT, and DNS underneath.
- Name resolution, forwarding, and policy are separate hops in the path.
- A network issue is not understood until you can describe where the next packet should go.

## Lab Focus
Use the lab to prove how service exposure, DNS, and network policy change in Kubernetes.
- Key commands:
  - `kubectl create ns net-mig`
  - `kubectl -n net-mig create deployment web --image=nginx:1.27-alpine`
  - `kubectl -n net-mig expose deployment web --port=80 --name web`
- Finish only when:
  - DNS/service access success before deny.
  - Access blocked after deny.

## Common Mistakes
- Changing app config before proving the packet path.
- Treating DNS, routing, and firewall behavior as one problem.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Storage Migration](../08-storage-migration/README.md).
