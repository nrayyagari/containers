# Persistence Strategies

## What It Is
Persistence Strategies covers How to separate ephemeral state from durable state.

## Why It Matters
It matters because state bugs usually surface late and are expensive to recover from.

## Key Points
- Not all data needs the same durability target.
- Separate ephemeral state, restart-safe state, and recovery-critical state deliberately.
- The storage choice should match the failure and recovery expectations of the workload.

## Practice Check
- Write a small file, restart the container, and confirm whether the data survived for the reason you expected.
- Use `docker inspect`, `mount`, `df`, or `df -i` to prove what backend is actually in use.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Inode Management](../09-inode-management/README.md).
