# Authentication

## What It Is
Authentication covers How registries authorize pull and push actions.

## Why It Matters
It matters because every pull and push is part of the software supply chain.

## Key Points
- Registry auth decides who may push, pull, or administer content.
- Authentication and authorization are separate concerns even when one token carries both.
- Image pull failures often look like network failures until auth is checked directly.

## Practice Check
- Inspect one image by tag and by digest so the difference becomes concrete.
- Use `skopeo inspect`, `curl /v2/`, or a registry UI to verify what object really exists.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Push Pull](../05-push-pull/README.md).
