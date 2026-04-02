# Dockerfile

## What It Is
Dockerfile covers How a Dockerfile defines image content and runtime defaults.

## Why It Matters
It matters because most day-to-day Docker mistakes are object-lifecycle mistakes.

## Key Points
- Every build step leaves filesystem or metadata history behind.
- Instruction order affects size, cache reuse, and traceability.
- Treat the image as a supply-chain artifact, not as a zip file with a tag.

## Lab Focus
Use the lab to prove how a Dockerfile defines image content and runtime defaults.
- Key commands:
  - `docker build -t dbk-lab:latest /tmp/dbk-lab`
  - `docker run --rm dbk-lab:latest`
  - `docker image inspect dbk-lab:latest | head -n 20`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Trusting the tag without checking the actual artifact or digest.
- Blaming runtime behavior that was baked into the image earlier.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Docker Compose](../07-docker-compose/README.md).
