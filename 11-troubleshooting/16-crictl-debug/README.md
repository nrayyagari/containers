# Crictl Debug

## What It Is
Crictl Debug covers How to inspect kubelet-facing container state through CRI tools.

## Why It Matters
It matters because fast recovery depends on asking the next correct question.

## Key Points
- Runtime stacks are layered and each layer has a different job.
- High-level managers handle images and lifecycle; low-level runtimes create the process.
- Use tools that match the layer that owns the workload.

## Practice Check
- Start with the least disruptive signal available.
- Build a short timeline before you touch restart or cleanup commands.

## Common Mistakes
- Collapsing several runtime layers into 'Docker is broken'.
- Using the wrong CLI for the layer that owns the workload.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Nerdctl Debug](../17-nerdctl-debug/README.md).
