# Mirrors Caching

## What It Is
Mirrors Caching covers How mirrors reduce latency and upstream dependency.

## Why It Matters
It matters because every pull and push is part of the software supply chain.

## Key Points
- Mirrors reduce latency, rate limits, and external dependency.
- A mirror helps only if clients are actually configured to use it.
- Cache freshness and fallback behavior matter as much as raw speed.

## Practice Check
- Inspect one image by tag and by digest so the difference becomes concrete.
- Use `skopeo inspect`, `curl /v2/`, or a registry UI to verify what object really exists.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Content Trust](../07-content-trust/README.md).
