# Exit Codes

## Context & Problem
This topic explains how process exit codes separate app crashes from platform problems. In production, this matters because fast recovery depends on collecting the right evidence before changing the system.

## First Principles
- Troubleshooting starts by proving which layer is healthy and which one is not.
- The best command is the one that answers the next question without mutating the system.
- A timeline plus one hard signal is usually worth more than a long list of disconnected outputs.

## Production Implementation
Use this topic to build an evidence hierarchy. Start with the least disruptive observation that can narrow the problem and only move to invasive tools once the current evidence no longer explains the symptom.

## Troubleshooting Approach
Keep moving from outer evidence to inner evidence: symptoms, logs, resource state, network state, runtime state, and finally invasive inspection. That preserves both signal and safety during an incident.

## Evolution & Alternatives
Troubleshooting used to be dominated by host access and manual inspection. Modern platforms added more layers, which is why disciplined evidence collection is even more important today.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Start with the least disruptive evidence source and only move deeper when the current signal no longer explains the symptom.
- Build a small timeline of what changed, what failed first, and what evidence proves that ordering.
- Avoid cleanup or restart actions until you can explain what question they would answer.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Core Dumps](../09-core-dumps/README.md).
