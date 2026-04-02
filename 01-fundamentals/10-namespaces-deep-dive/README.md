# Namespaces Deep Dive

## What It Is
Namespaces Deep Dive covers How each namespace type behaves and where boundaries can leak.

## Why It Matters
It matters because everything above this layer depends on these kernel boundaries behaving exactly as expected.

## Key Points
- Each namespace type isolates one category of resources, not everything.
- PID and network namespaces are usually the easiest places to prove isolation.
- Namespaces alone are not a complete container boundary; cgroups and security controls still matter.

## Lab Focus
Use the lab to prove how each namespace type behaves and where boundaries can leak.
- Key commands:
  - `docker run -d --name ns-lab alpine:3.20 sleep 300`
  - `ps -ef | head -n 10`
  - `docker exec ns-lab ps -ef`
- Finish only when:
  - All steps executed without unresolved errors.
  - You can explain observed behavior from first principles.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Cgroups Deep Dive](../11-cgroups-deep-dive/README.md).
