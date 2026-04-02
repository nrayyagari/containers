# Dive

## What It Is
Dive covers How Dive visualizes image layers and efficiency.

## Why It Matters
It matters because tool choice decides which layer you can actually observe.

## Key Points
- Tool choice should follow backend authority, not habit.
- A Docker-like CLI does not mean Docker semantics underneath.
- Good operators know what layer a tool exposes and what it hides.

## Practice Check
- State which backend the tool talks to before you run it.
- Compare the tool output with one lower-level source so you see what it abstracts.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Labs Container Toolkit](../10-labs-container-toolkit/README.md).
