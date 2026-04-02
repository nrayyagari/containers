# cgroups v2

## What It Is
cgroups v2 covers What the unified cgroup hierarchy changes for operators.

## Why It Matters
It matters because advanced features solve real problems but add real operational cost.

## Key Points
- cgroups control resources at the kernel level, not at the application level.
- Throttling, reclaim pressure, and OOM kills are observable signs of enforcement.
- cgroup v2 unifies the hierarchy and makes controller behavior more consistent.

## Practice Check
- List the host prerequisites before trying the feature.
- Name one clear benefit and one clear cost before adopting it.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Fuse Overlayfs](../04-fuse-overlayfs/README.md).
