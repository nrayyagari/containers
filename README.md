# Containers Learning Repository

This repository teaches containers from first principles. The target is not command recall; the target is being able to explain what the system is doing, what can fail, and what signal proves it.

## How To Use It
1. Start with `01-fundamentals` unless you already understand kernel and runtime boundaries well.
2. Read `README.md` before `LAB.md` so the commands have context.
3. Keep notes in this format: what it is, what can fail, what signal proves it.

## Learning Path
### 01 - Fundamentals
Kernel primitives that make containers possible.
- [Module README](./01-fundamentals/README.md)

### 02 - Docker Basics
The Docker object model and daily workflow.
- [Module README](./02-docker-basics/README.md)

### 03 - Image Building
How to build small, reproducible, secure images.
- [Module README](./03-image-building/README.md)

### 04 - Container Runtimes
The runtime stack from OCI contracts to running processes.
- [Module README](./04-container-runtimes/README.md)

### 05 - Networking
Packet flow, reachability, and service identity.
- [Module README](./05-networking/README.md)

### 06 - Storage
Persistent data, mounts, and filesystem trade-offs.
- [Module README](./06-storage/README.md)

### 07 - Security
Container hardening from image build to runtime policy.
- [Module README](./07-security/README.md)

### 08 - Registry
Image distribution, provenance, and lifecycle control.
- [Module README](./08-registry/README.md)

### 09 - Orchestration Basics
Control loops that manage containers at fleet scale.
- [Module README](./09-orchestration-basics/README.md)

### 10 - Best Practices
Habits that make container systems safer and cheaper.
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
How Docker-era workloads change in Kubernetes.
- [Module README](./14-migration-to-k8s/README.md)

## Standard
- You can trace a workload from image build to runtime execution.
- You can separate image, runtime, network, storage, and policy failures.
- You can choose the first diagnostic step with intent instead of guessing.
