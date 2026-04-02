# crictl

## What It Is
crictl covers How crictl speaks CRI for Kubernetes node debugging.

## Why It Matters
It matters because tool choice decides which layer you can actually observe.

## Key Points
- Runtime stacks are layered and each layer has a different job.
- High-level managers handle images and lifecycle; low-level runtimes create the process.
- Use tools that match the layer that owns the workload.

## Practice Check
- State which backend the tool talks to before you run it.
- Compare the tool output with one lower-level source so you see what it abstracts.

## Common Mistakes
- Collapsing several runtime layers into 'Docker is broken'.
- Using the wrong CLI for the layer that owns the workload.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Skopeo](../05-skopeo/README.md).
