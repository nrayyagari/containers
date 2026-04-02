# Layer Caching

## Context & Problem
This topic explains how layer cache hits and misses affect build speed and reproducibility. In production, this matters because the image you build becomes the artifact every runtime and every rollback depends on.

## First Principles
- Container storage has multiple lifecycles: image layers, writable layers, volumes, and external storage backends.
- Copy-on-write and overlay behavior can change both performance and the meaning of a write operation.
- Durability depends on where data lives, not on whether the application wrote it successfully once.

## Production Implementation
Make build inputs explicit and deterministic. The production question is always the same: can you explain exactly what ended up in the image, why it is there, and how you would rebuild it consistently?

## Troubleshooting Approach
Start with direct evidence at the layer this topic controls, then expand outward only if the observed state matches expectations.

## Evolution & Alternatives
BuildKit, better caching, and multi-stage design improved both speed and security, but the timeless lesson is still to publish only what you are willing to defend in production.

## Lab Tie-In
Use the lab to prove the mechanism, not just to finish a list of commands. Before you begin, decide which output line or state change will prove the concept above is real.

### Commands You Will See
- `docker build -t img-lab:latest /tmp/img-lab`
- `docker run --rm img-lab:latest`
- `docker history img-lab:latest`

### What Success Looks Like
- All steps executed without unresolved errors.
- You can explain observed behavior from first principles.
- You identified one failure mode and first diagnostic action.

### Questions To Answer After The Lab
- Which rebuild step demonstrates cache hit or invalidation most clearly?
- What CI latency/cost issue appears from poor layer ordering?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Base Images](../05-base-images/README.md).
