# Rootless Mode

## What It Is
Rootless Mode covers How rootless execution changes privilege, storage, and networking behavior.

## Why It Matters
It matters because advanced features solve real problems but add real operational cost.

## Key Points
- Container security is layered; no single flag makes a workload safe.
- Least privilege means reducing what the process can do and what you trust it with.
- A security control is only useful if you can explain what it blocks.

## Practice Check
- List the host prerequisites before trying the feature.
- Name one clear benefit and one clear cost before adopting it.

## Common Mistakes
- Loosening every control at once instead of identifying the blocking layer.
- Treating scanning or signing as a substitute for runtime hardening.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [User Namespaces](../02-user-namespaces/README.md).
