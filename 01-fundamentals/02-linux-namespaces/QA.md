# Linux Namespaces Q&A

## Context And Problem

This note captures a practical Q&A path for understanding Linux namespaces from first principles, with emphasis on the namespaces that are easiest to observe in containers: `uts`, `pid`, and `mnt`.

The goal is not to memorize namespace names. The goal is to be able to answer:

- What does this namespace isolate?
- What command proves that isolation?
- What output line is the proof?
- How does this appear in a real container?

## First Principles

### Q: Are namespaces only for containers?

A: No. Containers use namespaces heavily, but ordinary Linux processes can also run in separate namespaces. `systemd` services, sandbox tools, and debugging tools can all use namespaces directly.

### Q: What is a namespace in one sentence?

A: A namespace gives a process its own view of one category of system resources.

### Q: Which namespaces are easiest to understand first?

A: Start in this order:

1. `uts`
2. `pid`
3. `mnt`
4. `net`

These are easiest because they produce visible differences with simple commands.

## UTS Namespace

### Q: What does `uts` mean in practice?

A: It controls system identity fields, mainly the hostname seen by a process.

### Q: What is the simplest mental model for `uts`?

A: `uts` answers: "What machine name does this process think it is on?"

### Q: What is the easiest way to observe `uts` isolation?

A: Check the hostname inside and outside a container.

```bash
hostname
ls -l /proc/self/ns/uts
sudo lsns -t uts
```

### Q: What does output like `uts:[4026532300]` mean?

A: That number is the kernel's identifier for that specific UTS namespace.

- Same `uts:[...]` value: same UTS namespace
- Different `uts:[...]` value: different UTS namespace

### Q: Why did `readlink /proc/<pid>/ns/uts` show nothing?

A: These namespace entries behave like symlinks for tools such as `ls -l`, but `readlink` is not always useful here. Use:

```bash
ls -l /proc/1/ns/uts
ls -l /proc/<pid>/ns/uts
```

## PID Namespace

### Q: What problem does a PID namespace solve?

A: It gives a process a different process list and different PID numbering from the host.

### Q: What is the simplest mental model for `pid`?

A: `pid` answers: "Which processes do I see, and what numbers do they have?"

### Q: Why is PID 1 inside a container important?

A: Every PID namespace has its own PID 1. That process is special because it is the root of that namespace's process tree and is responsible for proper signal handling and child reaping.

### Q: Can the same real process have different PIDs?

A: Yes.

- On the host, a container process might be PID `71184`
- Inside the container, that same process might be PID `1`

The host PID is the global system view. The container PID is the namespace-local view.

### Q: Can two containers both have a PID 1?

A: Yes. Each PID namespace has its own numbering, so every container can have its own PID `1`.

### Q: I do not have `ps` inside a minimal container. How do I inspect PID namespaces anyway?

A: Use `/proc`.

```bash
echo $$
cat /proc/self/status | grep '^Pid:\|^PPid:\|^NSpid:'
ls -l /proc/self/ns/pid
ls /proc | grep '^[0-9]' | head
```

### Q: If `NSpid:` shows only one number, is that wrong?

A: No. Do not over-focus on that field. The clearer checks are:

```bash
ls -l /proc/self/ns/pid
sudo lsns -t pid
```

### Q: How do I compare the host and a running nginx container?

A: On the host:

```bash
docker inspect -f '{{.State.Pid}} {{.Name}}' <nginx-container>
ls -l /proc/1/ns/pid
ls -l /proc/$(docker inspect -f '{{.State.Pid}}' <nginx-container>)/ns/pid
```

Inside the container:

```bash
echo $$
cat /proc/1/status | grep '^Pid:\|^PPid:'
ls -l /proc/1/ns/pid
```

If the namespace IDs differ from the host, the container is in a different PID namespace.

## PID 1, Docker, ENTRYPOINT, and CMD

### Q: What is PID 1 of a container?

A: The first process started inside the container's PID namespace.

In Docker terms, it is usually the final command built from:

- `ENTRYPOINT`
- `CMD`

### Q: What do `ENTRYPOINT` and `CMD` literally mean?

A: Practical meaning:

- `ENTRYPOINT`: the main executable the image is built around
- `CMD`: the default arguments for that executable, or the default command if no `ENTRYPOINT` exists

Short rule:

- `ENTRYPOINT` says what to run
- `CMD` says how to run it by default

### Q: Why does Docker have both?

A: To separate image identity from default behavior.

- `ENTRYPOINT` keeps the image centered on one program
- `CMD` lets users override default arguments without replacing the whole command

### Q: Can I override `CMD` and `ENTRYPOINT` from the CLI?

A: Yes, but in different ways.

- Trailing arguments override `CMD`
- `--entrypoint` overrides `ENTRYPOINT`

Example image:

```dockerfile
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
```

Examples:

```bash
docker run mynginx
docker run mynginx -T
docker run --entrypoint sh mynginx -c 'echo hello'
```

### Q: Does whatever Docker runs become PID 1?

A: The final top-level process Docker launches becomes PID 1 inside the container.

Important nuance:

- if Docker launches `nginx` directly, `nginx` is PID 1
- if Docker launches a shell script, the shell script is PID 1 unless it uses `exec`

### Q: Why does `exec` matter in entrypoint scripts?

A: `exec` replaces the shell process with the real application instead of spawning it as a child.

Broken entrypoint:

```sh
#!/bin/sh
nginx -g 'daemon off;'
```

Result:

- shell script stays PID 1
- `nginx` is a child process

Correct entrypoint:

```sh
#!/bin/sh
exec nginx -g 'daemon off;'
```

Result:

- shell is replaced
- `nginx` becomes PID 1

### Q: What does `exec "$@"` mean?

A: It means:

- take all arguments passed to the script
- run them as the command
- replace the current shell process with that command

Example:

```sh
#!/bin/sh
exec "$@"
```

If the script receives:

```bash
nginx -g 'daemon off;'
```

then it effectively runs:

```bash
exec nginx -g 'daemon off;'
```

## Mount Namespace and OverlayFS

### Q: What is a mount namespace?

A: It gives a process its own view of mounted filesystems.

Simple mental model:

- `uts`: what hostname do I see?
- `pid`: what processes do I see?
- `mnt`: what filesystem tree do I see?

### Q: What does `findmnt -N <pid>` show?

A: It shows the mount tree seen by that process's mount namespace.

If `findmnt -N 60793` shows `/` as `overlay`, you are looking at the container's private filesystem view, not the host's root filesystem.

### Q: What is `overlayfs`?

A: It is a Linux filesystem type that merges multiple directory trees into one visible filesystem tree.

### Q: What is `overlay` then?

A: `overlay` is the mounted filesystem type you see in tools such as `findmnt`. In practice:

- `overlayfs` = the kernel filesystem mechanism
- `overlay` = the mounted filesystem shown by tools

### Q: Is `overlayfs` just another filesystem like `ext4`?

A: Yes, with an important difference.

- `ext4` stores one normal filesystem tree on disk
- `overlayfs` presents one merged tree built from other directories

### Q: What are lower, upper, and merged layers?

A: OverlayFS combines:

- `lowerdir`: read-only base layers
- `upperdir`: writable changes
- merged mount: the final combined view shown to the process

### Q: When you say image layers stay read-only, do you mean Docker image layers?

A: Yes. In container use, the lower read-only layers are usually the container image layers.

### Q: Is OverlayFS combining `/var/lib/docker` and `/var/lib/containerd`?

A: No. OverlayFS combines directory trees, not "Docker" and "containerd" as concepts.

The host paths are different storage locations with different roles:

- `/var/lib/containerd/...`
  - usually image snapshots and layer data used to build the container root filesystem
- `/var/lib/docker/...`
  - usually Docker metadata, container config files, and persistent volumes

### Q: What did this `findmnt` output mean?

If you see:

```text
/                 overlay              overlay ...
... lowerdir=/var/lib/containerd/...
/etc/resolv.conf /var/lib/docker/containers/<id>/resolv.conf
/data/db         /var/lib/docker/volumes/<id>/_data
```

the interpretation is:

- `/` is the container root filesystem assembled by OverlayFS
- `lowerdir=/var/lib/containerd/...` points to image-layer backing data
- `/etc/hostname`, `/etc/hosts`, `/etc/resolv.conf` are Docker-managed per-container files
- `/data/db` and similar paths are Docker volumes mounted into the container

### Q: What is the short mental model for this mount setup?

A:

- `containerd` stores image layers
- `overlayfs` merges them into the container's `/`
- `docker` adds metadata files and volumes on top

## Troubleshooting Approach

### Q: Which namespace should I inspect first?

A: Start with the one that answers the symptom fastest:

- hostname issue: `uts`
- missing or extra processes: `pid`
- strange filesystem view: `mnt`
- interface, route, or port issue: `net`

### Q: Which commands give the most learning value per namespace?

A:

For `uts`:

```bash
hostname
ls -l /proc/self/ns/uts
sudo lsns -t uts
```

For `pid`:

```bash
echo $$
ls -l /proc/self/ns/pid
sudo lsns -t pid
```

For `mnt`:

```bash
findmnt -N <pid>
ls -l /proc/<pid>/ns/mnt
```

## Evolution And Alternatives

### Q: Why do systemd services often use only some namespaces rather than all of them?

A: Because `systemd` usually applies namespaces as targeted hardening, not as full containerization.

Examples:

- `mnt`: useful for restricting filesystem visibility
- `uts`: useful for identity isolation

Many host services still need the host's normal process tree, network stack, or user model, so using all namespaces would be unnecessary or disruptive.

## Next Steps

After this Q&A, the best next learning sequence is:

1. Prove `uts` isolation with hostname checks
2. Prove `pid` isolation by comparing host and container PIDs
3. Prove `mnt` isolation with `findmnt -N <pid>`
4. Add `net` namespace checks with `ip addr`, `ip route`, and `ss`

## References

- Linux OverlayFS documentation: https://docs.kernel.org/filesystems/overlayfs.html
- Docker OverlayFS storage driver: https://docs.docker.com/engine/storage/drivers/overlayfs-driver/
- Docker volumes: https://docs.docker.com/engine/storage/volumes/
- Datadog Security Labs, container namespaces: https://securitylabs.datadoghq.com/articles/container-security-fundamentals-part-2/
