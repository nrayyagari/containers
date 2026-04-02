# User Namespaces

## What It Is
User Namespaces covers How user namespaces underpin stronger isolation and rootless patterns.

## Why It Matters
It matters because advanced features solve real problems but add real operational cost.

## Key Points
- Each namespace type isolates one category of resources, not everything.
- PID and network namespaces are usually the easiest places to prove isolation.
- Namespaces alone are not a complete container boundary; cgroups and security controls still matter.

## Practice Check
- List the host prerequisites before trying the feature.
- Name one clear benefit and one clear cost before adopting it.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [cgroups v2](../03-cgroups-v2/README.md).
