# Security Hardening

## What It Is
Security Hardening covers How to reduce privilege and patch exposure.

## Why It Matters
It matters because small shortcuts here become recurring reliability and security problems later.

## Key Points
- Container security is layered; no single flag makes a workload safe.
- Least privilege means reducing what the process can do and what you trust it with.
- A security control is only useful if you can explain what it blocks.

## Practice Check
- Apply the practice to one real image or service instead of a hypothetical one.
- Write down the operational benefit you expect and how you would verify it.

## Common Mistakes
- Loosening every control at once instead of identifying the blocking layer.
- Treating scanning or signing as a substitute for runtime hardening.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Multi Stage Builds](../04-multi-stage-builds/README.md).
