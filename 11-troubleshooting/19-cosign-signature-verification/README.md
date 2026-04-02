# Cosign Signature Verification

## What It Is
Cosign Signature Verification covers How to verify image signatures before you trust an artifact.

## Why It Matters
It matters because fast recovery depends on asking the next correct question.

## Key Points
- Container security is layered; no single flag makes a workload safe.
- Least privilege means reducing what the process can do and what you trust it with.
- A security control is only useful if you can explain what it blocks.

## Practice Check
- Start with the least disruptive signal available.
- Build a short timeline before you touch restart or cleanup commands.

## Common Mistakes
- Loosening every control at once instead of identifying the blocking layer.
- Treating scanning or signing as a substitute for runtime hardening.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Garbage Collection Cleanup](../20-garbage-collection-cleanup/README.md).
