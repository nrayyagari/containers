# Content Trust

## What It Is
Content Trust covers How signing and verification fit into registry workflows.

## Why It Matters
It matters because every pull and push is part of the software supply chain.

## Key Points
- Content trust is about verifying origin and integrity before runtime.
- Signing answers who produced the artifact; scanning answers what is inside it.
- Those are complementary controls, not replacements for each other.

## Practice Check
- Inspect one image by tag and by digest so the difference becomes concrete.
- Use `skopeo inspect`, `curl /v2/`, or a registry UI to verify what object really exists.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Garbage Collection](../08-garbage-collection/README.md).
