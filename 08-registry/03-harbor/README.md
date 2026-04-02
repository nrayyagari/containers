# Harbor

## What It Is
Harbor is a registry platform built around image storage plus operational controls such as auth, projects, scanning, signing, and retention.

## Why It Matters
Registry policy and provenance directly affect what can be deployed and trusted.

## Key Points
- Harbor adds project, policy, scanning, signing, and retention workflows around registry storage.
- Its value is operational control, not just storing more images.
- Teams use it when provenance and governance matter as much as availability.

## Practice Check
- Inspect one image by tag and by digest so the difference becomes concrete.
- Use `skopeo inspect`, `curl /v2/`, or a registry UI to verify what object really exists.

## Common Mistakes
- Thinking of Harbor as just image storage and ignoring policy features.
- Using tags as identity when the real artifact identity is the digest.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Authentication](../04-authentication/README.md).
