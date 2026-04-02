# Push Pull

## What It Is
Push Pull covers What actually happens during image upload and download.

## Why It Matters
It matters because every pull and push is part of the software supply chain.

## Key Points
- Push and pull operate on blobs and manifests, not on one giant opaque file.
- The client may reuse already present layers, so transfer behavior is incremental.
- Knowing what moved and what did not is key during distribution issues.

## Practice Check
- Inspect one image by tag and by digest so the difference becomes concrete.
- Use `skopeo inspect`, `curl /v2/`, or a registry UI to verify what object really exists.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Mirrors Caching](../06-mirrors-caching/README.md).
