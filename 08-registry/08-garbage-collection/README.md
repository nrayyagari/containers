# Garbage Collection

## What It Is
Garbage Collection covers How registries reclaim unreferenced blobs safely.

## Why It Matters
It matters because every pull and push is part of the software supply chain.

## Key Points
- Registry garbage collection removes unreferenced blobs, not whatever simply looks old.
- Safe cleanup depends on understanding tag, manifest, and layer relationships.
- Aggressive cleanup without that model can break future pulls and rollbacks.

## Practice Check
- Inspect one image by tag and by digest so the difference becomes concrete.
- Use `skopeo inspect`, `curl /v2/`, or a registry UI to verify what object really exists.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Registry Api](../09-registry-api/README.md).
