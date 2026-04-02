# gVisor and Kata

## What It Is
gVisor and Kata covers How sandboxed runtimes trade performance for stronger isolation.

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
Then continue to [Firecracker MicroVMs](../09-firecracker-microvm/README.md).
