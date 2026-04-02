# User Namespace Mapping

## What It Is
User Namespace Mapping covers How container IDs map to less-privileged host IDs.

## Why It Matters
It matters because one weak control can widen the blast radius of every other mistake.

## Key Points
- Each namespace type isolates one category of resources, not everything.
- PID and network namespaces are usually the easiest places to prove isolation.
- Namespaces alone are not a complete container boundary; cgroups and security controls still matter.

## Practice Check
- Change one security control at a time and explain what action is now blocked.
- Use inspection output as evidence instead of assuming the policy is active.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Rootless Containers](../02-rootless-containers/README.md).
