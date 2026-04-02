# Images

## What It Is
Images covers How images are pulled, tagged, stored, and inspected.

## Why It Matters
It matters because most day-to-day Docker mistakes are object-lifecycle mistakes.

## Key Points
- Every build step leaves filesystem or metadata history behind.
- Instruction order affects size, cache reuse, and traceability.
- Treat the image as a supply-chain artifact, not as a zip file with a tag.

## Lab Focus
Use the lab to prove how images are pulled, tagged, stored, and inspected.
- Key commands:
  - `docker pull alpine:3.20`
  - `docker run -d --name dk-lab alpine:3.20 sleep 300`
  - `docker inspect dk-lab --format "{{.Config.Image}} {{.State.Status}}"`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Trusting the tag without checking the actual artifact or digest.
- Blaming runtime behavior that was baked into the image earlier.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Containers](../03-containers/README.md).
