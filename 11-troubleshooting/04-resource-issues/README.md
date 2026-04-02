# Resource Issues

## What It Is
Resource Issues covers How to diagnose OOM kills, throttling, and pressure-related slowdowns.

## Why It Matters
It matters because fast recovery depends on asking the next correct question.

## Key Points
- Start with the least disruptive signal that answers the next question.
- Logs, metrics, runtime state, and packet evidence answer different questions.
- Restarting a component is not diagnosis.

## Practice Check
- Start with the least disruptive signal available.
- Build a short timeline before you touch restart or cleanup commands.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Process Analysis](../05-process-analysis/README.md).
