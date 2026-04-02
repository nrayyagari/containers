# Dive Image Analysis

## What It Is
Dive Image Analysis covers How to inspect image layers and wasted space before runtime.

## Why It Matters
It matters because fast recovery depends on asking the next correct question.

## Key Points
- Every build step leaves filesystem or metadata history behind.
- Instruction order affects size, cache reuse, and traceability.
- Treat the image as a supply-chain artifact, not as a zip file with a tag.

## Practice Check
- Start with the least disruptive signal available.
- Build a short timeline before you touch restart or cleanup commands.

## Common Mistakes
- Trusting the tag without checking the actual artifact or digest.
- Blaming runtime behavior that was baked into the image earlier.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Cosign Signature Verification](../19-cosign-signature-verification/README.md).
