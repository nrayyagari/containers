# Buildah

## What It Is
Buildah covers How Buildah builds OCI images without the Docker daemon model.

## Why It Matters
It matters because tool choice decides which layer you can actually observe.

## Key Points
- Every build step leaves filesystem or metadata history behind.
- Instruction order affects size, cache reuse, and traceability.
- Treat the image as a supply-chain artifact, not as a zip file with a tag.

## Practice Check
- State which backend the tool talks to before you run it.
- Compare the tool output with one lower-level source so you see what it abstracts.

## Common Mistakes
- Trusting the tag without checking the actual artifact or digest.
- Blaming runtime behavior that was baked into the image earlier.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [nerdctl](../03-nerdctl/README.md).
