# Firecracker MicroVMs

## What It Is
Firecracker MicroVMs covers How microVMs bridge the gap between containers and VMs.

## Why It Matters
It matters because advanced features solve real problems but add real operational cost.

## Key Points
- Advanced features are trade-offs, not automatic upgrades.
- Most of them change host assumptions around privilege, filesystem, or runtime support.
- Use them only when the default path is clearly insufficient.

## Practice Check
- List the host prerequisites before trying the feature.
- Name one clear benefit and one clear cost before adopting it.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Unix Domain Sockets](../10-uds-uds/README.md).
