# Registries

## Context & Problem
This topic explains how builders and runtimes interact with registries during push and pull. In production, this matters because the image you build becomes the artifact every runtime and every rollback depends on.

## First Principles
- A build is not just file packaging; it is a repeatable process for producing a runtime artifact with known contents.
- Every instruction influences either the filesystem, the metadata, or the cache behavior of the final image.
- Image quality is measured by reproducibility, traceability, size, and the absence of unintended content.

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
- Which artifact identity signal in this lab is strongest for release safety?
- What drift risk appears when relying on mutable tags only?

## Next Steps
Run [LAB.md](./LAB.md) and do not mark it complete until you can explain both the mechanism and the failure mode.
After that, continue to [Tags](../08-tags/README.md).
