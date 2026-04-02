# Trivy and Snyk

## What It Is
Trivy and Snyk covers How common image scanners differ in workflow and findings.

## Why It Matters
It matters because one weak control can widen the blast radius of every other mistake.

## Key Points
- Different scanners can report different results for the same image.
- The important question is which findings are real, reachable, and worth action.
- Scanning is useful only when it feeds a patch, risk-acceptance, or blocking decision.

## Practice Check
- Change one security control at a time and explain what action is now blocked.
- Use inspection output as evidence instead of assuming the policy is active.

## Common Mistakes
- Changing several things before you know which boundary is failing.
- Finishing the exercise without being able to explain the proof signal.

## Next
Prove the behavior in a disposable environment before moving on.
Then continue to [Image Signing](../09-image-signing/README.md).
