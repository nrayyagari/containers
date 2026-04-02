# Linux Capabilities

## What It Is
Linux Capabilities covers How root privileges are split into smaller permission sets.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- Container security is layered; no single flag makes a workload safe.
- Least privilege means reducing what the process can do and what you trust it with.
- A security control is only useful if you can explain what it blocks.

## Lab Focus
Use the lab to prove how root privileges are split into smaller permission sets.
- Key commands:
  - `docker run --rm --cap-drop ALL alpine:3.20 sh -c "id && ping -c1 127.0.0.1 || true"`
  - `docker run --rm --cap-drop ALL --cap-add NET_RAW alpine:3.20 ping -c1 127.0.0.1`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Loosening every control at once instead of identifying the blocking layer.
- Treating scanning or signing as a substitute for runtime hardening.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Seccomp Apparmor](../09-seccomp-apparmor/README.md).
