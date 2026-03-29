# Containers - A Comprehensive Learning Journey

> From Linux kernel fundamentals to Kubernetes readiness

## Table of Contents

1. [Fundamentals](#01-fundamentals)
2. [Docker Basics](#02-docker-basics)
3. [Image Building](#03-image-building)
4. [Container Runtimes](#04-container-runtimes)
5. [Networking](#05-networking)
6. [Storage](#06-storage)
7. [Security](#07-security)
8. [Registry](#08-registry)
9. [Orchestration Basics](#09-orchestration-basics)
10. [Best Practices](#10-best-practices)
11. [Troubleshooting](#11-troubleshooting)
12. [Tools](#12-tools)
13. [Advanced](#13-advanced)
14. [Migration to Kubernetes](#14-migration-to-k8s)

---

## 01 - Fundamentals
*Linux kernel mechanisms that make containers possible*

| Topic | Description |
|-------|-------------|
| 01-virtualization-basics | Evolution of virtualization, hypervisors vs containers |
| 02-linux-namespaces | IPC, Mount, Network, PID, User, UTS namespaces |
| 03-control-groups-cgroups | Resource limits: CPU, Memory, I/O, Blkio |
| 04-union-filesystems | OverlayFS, AUFS, layer mechanics |
| 05-process-isolation | Container = isolated process on host |
| 06-kernel-features | Namespace APIs, cgroup v1/v2 |
| 07-container-vs-vm | Key architectural differences |
| 08-linux-capabilities | CAP_NET_BIND_SERVICE, privilege dropping |
| 09-seccomp-apparmor | Syscall filtering, mandatory access control |
| 10-namespaces-deep-dive | Each namespace type in exhaustive detail |
| 11-cgroups-deep-dive | Controllers, hierarchies, resource control |
| 12-isolation-summary | Putting it all together |

---

## 02 - Docker Basics
*Mastering the Docker ecosystem*

| Topic | Description |
|-------|-------------|
| 01-cli-basics | docker run, ps, exec, logs, etc. |
| 02-images | pull, tag, rmi, inspect |
| 03-containers | create, start, stop, rm, logs |
| 04-volumes | -v, --mount, volume management |
| 05-networking-basics | bridge, host, none networks |
| 06-dockerfile | Writing Dockerfiles from scratch |
| 07-docker-compose | Multi-container orchestration |
| 08-docker-daemon | Architecture, socket, API |
| 09-storage-driver | overlay2, devicemapper, vfs |
| 10-compose-yaml | compose.yaml syntax |

---

## 03 - Image Building
*Creating efficient, secure container images*

| Topic | Description |
|-------|-------------|
| 01-dockerfile-basics | Anatomy of a Dockerfile |
| 02-instructions | RUN, COPY, ADD, ENV, WORKDIR, etc. |
| 03-multi-stage-builds | Reduce image size dramatically |
| 04-layer-caching | Optimize build cache |
| 05-base-images | alpine, debian, scratch, distroless |
| 06-best-practices | Security, size, maintainability |
| 07-registries | Where to store images |
| 08-tags | Versioning, latest, immutable tags |
| 09-build-args | ARG, build-time variables |
| 10-build-secrets | Secrets without leaking in layers |

---

## 04 - Container Runtimes
*Understanding the runtime hierarchy*

| Topic | Description |
|-------|-------------|
| 01-runc | OCI low-level runtime, container creation |
| 02-containerd | High-level runtime, image management |
| 03-cri | Container Runtime Interface |
| 04-crio | Kubernetes-focused runtime |
| 05-docker-vs-containerd | Architecture evolution |
| 06-low-level-runtime | What actually creates containers |
| 07-high-level-runtime | Image pulls, container lifecycle |
| 08-shim-process | shimv2, containerd-shim |
| 09-oci-spec | Runtime spec, image spec |
| 10-runtime-classes | Configuring runtime classes |

---

## 05 - Networking
*Container networking deep dive*

| Topic | Description |
|-------|-------------|
| 01-bridge-networking | docker0 bridge, iptables |
| 02-host-networking | Host network mode |
| 03-overlay-networking | Docker Swarm, VXLAN |
| 04-macvlan-ipvlan | Direct network attachment |
| 05-dns-service-discovery | Embedded DNS, service names |
| 06-port-mapping | -p flag, host binding |
| 07-network-namespaces | Linux network namespaces |
| 08-docker-proxy | docker-proxy process |
| 09-iptables-rules | NAT, forwarding, filtering |
| 10-ipv6 | IPv6 in containers |

---

## 06 - Storage
*Persistent and ephemeral storage*

| Topic | Description |
|-------|-------------|
| 01-bind-mounts | Host directory mounting |
| 02-named-volumes | Docker-managed volumes |
| 03-tmpfs-mounts | In-memory storage |
| 04-volume-drivers | local, rexray, convoy |
| 05-storage-drivers-overlay | overlay2 driver |
| 06-nfs-volumes | Network filesystem volumes |
| 07-volume-permissions | uid/gid, chmod |
| 08-persistence-strategies | Data durability patterns |
| 09-inode-management | inode exhaustion |
| 10-backup-restore | Volume backup strategies |

---

## 07 - Security
*Hardening containers at every layer*

| Topic | Description |
|-------|-------------|
| 01-user-namespace-mapping | Map UID/GID ranges |
| 02-rootless-containers | Running without root |
| 03-drop-capabilities | Drop ALL, add only required |
| 04-seccomp-profiles | Syscall filtering |
| 05-apparmor-profiles | Mandatory access control |
| 06-selinux | Security-enhanced Linux |
| 07-image-scanning | Vulnerability detection |
| 08-trivy-snyk | Scanning tools |
| 09-image-signing | Content trust, signatures |
| 10-privileged-containers | Dangers and when needed |
| 11-security-best-practices | Defense in depth |
| 12-runtime-security | Runtime protection |

---

## 08 - Registry
*Managing container image distribution*

| Topic | Description |
|-------|-------------|
| 01-docker-hub | Public registry |
| 02-private-registry | Self-hosted registry |
| 03-harbor | Enterprise registry |
| 04-authentication | Token-based auth |
| 05-push-pull | Image push/pull |
| 06-mirrors-caching | Registry mirrors |
| 07-content-trust | Docker Content Trust |
| 08-garbage-collection | Cleaning up unused images |
| 09-registry-api | REST API |
| 10-artifact-management | OCI artifacts |

---

## 09 - Orchestration Basics
*Introduction to container orchestration*

| Topic | Description |
|-------|-------------|
| 01-what-is-orchestration | Why we need orchestrators |
| 02-service-discovery | Finding services dynamically |
| 03-load-balancing | Distributing traffic |
| 04-scaling | Horizontal/vertical scaling |
| 05-health-checks | Liveness, readiness probes |
| 06-self-healing | Auto-restart, replacement |
| 07-rollout-rollback | Deployment strategies |
| 08-config-management | ConfigMaps, secrets |
| 09-scheduling | Where to place containers |
| 10-reconciliation | Desired vs actual state |

---

## 10 - Best Practices
*Production-ready patterns*

| Topic | Description |
|-------|-------------|
| 01-image-size | Minimizing image footprint |
| 02-layer-optimization | Fewer layers, better caching |
| 03-security-hardening | CIS benchmarks |
| 04-multi-stage-builds | Minimal final images |
| 05-healthchecks | HEALTHCHECK instruction |
| 06-logging | Structured logging |
| 07-resource-limits | Memory, CPU limits |
| 08-immutable-tags | Pinning versions |
| 09-minimal-base-images | distroless, scratch |
| 10-ci-cd-integration | Pipeline best practices |

---

## 11 - Troubleshooting
*Debugging containers in production*

| Topic | Description |
|-------|-------------|
| 01-logs | docker logs, journalctl |
| 02-inside-container | nsenter, chroot |
| 03-network-debugging | ping, curl, netcat |
| 04-resource-issues | OOM, CPU throttling |
| 05-process-analysis | ps, pgrep, pstree |
| 06-disk-space | du, df, docker system df |
| 07-dns-issues | /etc/resolv.conf, dig |
| 08-exit-codes | Error code analysis |
| 09-core-dumps | gdb, ulimit |
| 10-tools-dive-ctop-sysdig | dive, ctop, sysdig |
| 11-strace-ltrace | Syscall tracing |
| 12-tcpdump-wireshark | Packet capture |
| 13-htop-top | Process monitoring |
| 14-sysdig-falco | Runtime security/syscalls |
| 15-prometheus-metrics | Metrics collection |
| 16-crictl-debug | CRI runtime debugging |
| 17-nerdctl-debug | containerd CLI debugging |
| 18-dive-image-analysis | Image layer analysis |
| 19-cosign-signature-verification | Signature verification |
| 20-garbage-collection-cleanup | docker system prune |

---

## 12 - Tools
*Alternative and complementary tools*

| Topic | Description |
|-------|-------------|
| 01-podman | Daemonless container engine |
| 02-buildah | Building images without Docker |
| 03-nerdctl | containerd CLI |
| 04-crictl | CRI-compatible CLI |
| 05-skopeo | Image inspection/sync |
| 06-docker-buildx | Extended build features |
| 07-kompose | Docker Compose to Kubernetes |
| 08-ctop | Container top |
| 09-dive | Image layer analysis |
| 10-labs-container-toolkit | Red Hat tools |

---

## 13 - Advanced
*Cutting-edge container technologies*

| Topic | Description |
|-------|-------------|
| 01-rootless-mode | Rootless containers in depth |
| 02-user-namespaces | Advanced mapping |
| 03-cgroups-v2 | Unified hierarchy |
| 04-fuse-overlayfs | FUSE-based overlay |
| 05-image-distribution | Distribution specs |
| 06-zfs-btrfs | Advanced filesystems |
| 07-efi-secure-boot | Secure boot integration |
| 08-gvisor-katata | Sandboxed containers |
| 09-firecracker-microvm | MicroVM runtime |
| 10-uds-uds | Unix domain sockets |

---

## 14 - Migration to Kubernetes
*Moving from standalone containers to K8s*

| Topic | Description |
|-------|-------------|
| 01-docker-to-containerd | Runtime transition |
| 02-cri-compatibility | CRI API |
| 03-image-format | OCI image spec |
| 04-pod-concept | Multi-container pods |
| 05-deployment-strategies | Rolling, blue-green, canary |
| 06-config-secrets | K8s ConfigMaps, Secrets |
| 07-networking-changes | K8s networking model |
| 08-storage-migration | PVs, PVCs, StorageClass |
| 09-service-mesh | Istio, Linkerd |
| 10-monitoring-observability | Prometheus, Jaeger |

---

## Learning Path

```
01-fundamentals ──► 02-docker-basics ──► 03-image-building ──► 04-container-runtimes
                           │                      │
                           ▼                      ▼
                     05-networking ◄──────── 06-storage
                           │
                           ▼
                     07-security ──────────► 08-registry
                           │
                           ▼
              ┌────────────┴────────────┐
              ▼                         ▼
       09-orchestration-basics    10-best-practices
              │
              ▼
         11-troubleshooting
              │
              ▼
         12-tools
              │
              ▼
         13-advanced
              │
              ▼
    14-migration-to-k8s
```

---

## Prerequisites

- Linux basics (processes, files, permissions)
- Command line familiarity
- Understanding of networking fundamentals (IP, ports, DNS)

## Quick Start

```bash
# Verify container environment
docker --version
containerd --version
runc --version

# Run your first container
docker run hello-world

# Explore available images
docker images
```

---

## Resources

- [Docker Documentation](https://docs.docker.com/)
- [OCI Specifications](https://opencontainers.org/specs/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Linux Kernel Namespaces](https://man7.org/linux/man-pages/man7/namespaces.7.html)
- [cgroup Documentation](https://www.kernel.org/doc/Documentation/cgroup-v2.txt)

---

## License

MIT
