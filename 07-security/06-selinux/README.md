# SELinux

## What It Is
SELinux covers How SELinux labels enforce mandatory separation.

## Why It Matters
It matters because one weak control can widen the blast radius of every other mistake.

## Key Points
- Container security is layered; no single flag makes a workload safe.
- Least privilege means reducing what the process can do and what you trust it with.
- A security control is only useful if you can explain what it blocks.

## Practice Check
- Change one security control at a time and explain what action is now blocked.
- Use inspection output as evidence instead of assuming the policy is active.

## Common Mistakes
- Loosening every control at once instead of identifying the blocking layer.
- Treating scanning or signing as a substitute for runtime hardening.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Image Scanning](../07-image-scanning/README.md).
