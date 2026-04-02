# Skopeo

## Context & Problem
This topic explains how Skopeo inspects and copies images without pulling them locally. In production, this matters because tool choice determines which layer you can actually observe and which assumptions remain hidden.

## First Principles
- Each tool exists because a different layer needs to be built, inspected, or debugged.
- A familiar-looking CLI does not guarantee the same backend, the same state model, or the same safe assumptions.
- Tool fluency matters only when it is tied to a clear mental model of the layer underneath.

## Production Implementation
Use the tool because its backend matches the system layer you care about, not because its UX is familiar. Good operators choose tools the same way they choose APIs: by authority and scope.

## Troubleshooting Approach
If a tool shows surprising results, verify what backend it is querying and whether that backend owns the objects you care about. A wrong-but-confident tool is more dangerous than an unavailable one.

## Evolution & Alternatives
The ecosystem diversified as build, runtime, registry, and Kubernetes concerns separated. Tool sprawl is the price of specialization, so clarity about scope matters more than CLI memorization.

## Practical Focus
There is no dedicated lab file for this topic, so practice it explicitly on a disposable system instead of reading passively.
- Run the tool only after you can say which backend it is querying and why that backend is authoritative for the question you have.
- Compare the tool output with one lower-level source so you can see what abstraction it adds or hides.
- Write down one situation where this tool is the right choice and one where it would mislead you.

## Next Steps
Practice the topic with real evidence before moving on. Reading without proving the behavior is not enough here.
After that, continue to [Docker Buildx](../06-docker-buildx/README.md).
