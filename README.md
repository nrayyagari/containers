# Containers Learning Repository

This repository teaches containers from first principles instead of starting with memorized commands. The goal is simple: after reading a topic and running its practice, you should be able to explain what the system is doing, what can fail, and which signal proves it.

## Context & Problem
Container knowledge is often fragmented. People know how to run an image or copy a Compose file, but they do not always know which Linux primitive, runtime boundary, or control-plane decision is responsible for the behavior they see. That gap becomes expensive during incidents and migrations.

## How To Use This Repository
1. Start with `01-fundamentals` and move in order unless you already understand the kernel and runtime layers deeply.
2. For every topic, read `README.md` first so you understand the problem and the mechanism before you touch commands.
3. If a `LAB.md` exists, treat it as proof work. Finish only when you can explain the observed output and the likely production failure mode.
4. Keep short notes for each topic: mechanism, first signal to check, and first safe diagnostic action.

## What Good Learning Looks Like
- You can explain a container as a set of kernel and runtime boundaries, not as a black box.
- You can separate image problems, runtime problems, network problems, storage problems, and policy problems instead of blending them together.
- You can say what changed when the platform becomes Kubernetes and why Docker-era assumptions stop being enough.

## Curriculum Map
### 01 - Fundamentals
Kernel primitives that make containers possible.
- [Module README](./01-fundamentals/README.md)

### 02 - Docker Basics
The Docker object model and daily operational workflow.
- [Module README](./02-docker-basics/README.md)

### 03 - Image Building
How to build small, reproducible, and secure images.
- [Module README](./03-image-building/README.md)

### 04 - Container Runtimes
The runtime stack from OCI contracts to running processes.
- [Module README](./04-container-runtimes/README.md)

### 05 - Networking
Container packet flow, connectivity, and service reachability.
- [Module README](./05-networking/README.md)

### 06 - Storage
Persistent data, mount semantics, and filesystem trade-offs.
- [Module README](./06-storage/README.md)

### 07 - Security
Container hardening from image build to runtime policy.
- [Module README](./07-security/README.md)

### 08 - Registry
Image distribution, provenance, and lifecycle control.
- [Module README](./08-registry/README.md)

### 09 - Orchestration Basics
The control loops that manage containers at fleet scale.
- [Module README](./09-orchestration-basics/README.md)

### 10 - Best Practices
Operational habits that make container systems safer and cheaper.
- [Module README](./10-best-practices/README.md)

### 11 - Troubleshooting
Evidence-first workflows for reducing incident MTTR.
- [Module README](./11-troubleshooting/README.md)

### 12 - Tools
The container tooling ecosystem beyond plain Docker.
- [Module README](./12-tools/README.md)

### 13 - Advanced
Isolation, performance, and runtime details beyond the defaults.
- [Module README](./13-advanced/README.md)

### 14 - Migration to Kubernetes
How Docker-era workloads change when the platform becomes Kubernetes.
- [Module README](./14-migration-to-k8s/README.md)

## Primary References Used To Verify Core Concepts
These official references informed the current docs pass and anchor the core runtime, build, and Kubernetes concepts used across the repository.
- https://docs.docker.com/build/building/multi-stage/
- https://docs.docker.com/build/building/secrets/
- https://docs.docker.com/reference/compose-file/
- https://docs.docker.com/engine/security/rootless/
- https://docs.docker.com/engine/storage/drivers/overlayfs-driver/
- https://kubernetes.io/docs/concepts/architecture/cri/
- https://kubernetes.io/docs/concepts/workloads/pods/
- https://kubernetes.io/docs/concepts/containers/runtime-class
- https://kubernetes.io/docs/concepts/configuration/secret/
- https://containerd.io/docs/
- https://docs.kernel.org/6.10/admin-guide/cgroup-v2.html

## Completion Standard
By the end of this repository, you should be able to trace a containerized workload from image build to runtime execution, explain which boundary is failing when something breaks, and choose the first diagnostic step with intent instead of guesswork.
