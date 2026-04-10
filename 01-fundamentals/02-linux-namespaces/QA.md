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

### Q: Does `ps` get its information from `/proc`?

A: Yes. `ps` primarily reads process information from the `/proc` filesystem.

Important wording:

- `/proc` is a virtual filesystem, not just a folder
- `/proc/1` is a directory inside that filesystem
- `/proc/1/status` is a file inside that filesystem

That is why PID namespace changes show up clearly through `/proc`.

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

### Q: Why did I still see host files after running `sudo nsenter -t <pid> -u sh`?

A: Because `-u` enters only the UTS namespace.

That changes only the hostname view. It does not change the filesystem view.

So this behavior is expected:

- `hostname` shows the container hostname
- `ls` still shows host files if you did not also enter the mount namespace

To see the container filesystem view too, include `-m`:

```bash
sudo nsenter -t <pid> -m -u sh
```

For a more complete "inside the container" view, include more namespaces:

```bash
sudo nsenter -t <pid> -m -p -u -n sh
```

## Network Namespace

### Q: What problem does a network namespace solve?

A: It gives a process its own network stack.

That includes its own:

- interfaces
- IP addresses
- routes
- port bindings

### Q: What is the simplest mental model for `net`?

A: `net` answers: "Which interfaces, addresses, routes, and listening ports do I see?"

### Q: What commands are the most useful for proving `net` isolation?

A:

```bash
ip addr
ip route
ss -lntup
ls -l /proc/self/ns/net
sudo lsns -t net
```

### Q: What is the clearest host-versus-container comparison for `net`?

A: Compare the namespace ID and interface list on the host and inside the container.

On the host:

```bash
docker inspect -f '{{.State.Pid}} {{.Name}}' <container>
ls -l /proc/1/ns/net
ls -l /proc/$(docker inspect -f '{{.State.Pid}}' <container>)/ns/net
```

Inside the container:

```bash
ip addr
ip route
ls -l /proc/self/ns/net
```

If the `net:[...]` values differ, the container is in a different network namespace.

### Q: What is a very common sign that a container is in a separate network namespace?

A: The container sees its own interface layout, often including `lo` and one `eth0`, while the host sees many other interfaces and routes.

### Q: What changes if the container uses `--network host`?

A: Then the container shares the host network namespace instead of getting its own one.

In that case:

- interface names match the host
- listening ports are in the host network stack
- `ls -l /proc/self/ns/net` from a shell in that container matches the host value

## Other Namespaces

### Q: What does the IPC namespace isolate?

A: Inter-process communication objects such as System V IPC and POSIX message queues.

Practical mental model:

- `ipc` answers: "Which shared memory segments, semaphores, and message queues do I see?"

### Q: What does the user namespace isolate?

A: User and group ID mappings and related privilege interpretation.

Practical meaning:

- a process can look like `root` inside the namespace
- while mapping to a non-root identity outside it

### Q: What does the cgroup namespace isolate?

A: The process's view of cgroup paths.

Practical meaning:

- tools inside the container see cgroup paths relative to the container's own view
- instead of the full host cgroup layout

### Q: What does the time namespace isolate?

A: Selected time offsets used by processes.

This is less common in beginner container work, but it exists as another namespace type.

## `nsenter`

### Q: What is `nsenter` used for?

A: `nsenter` starts a program inside one or more namespaces that already belong to an existing process.

This is especially useful for:

- debugging a running container
- comparing host view and container view
- inspecting namespaces even when container tools are minimal

### Q: What does this command mean?

```bash
sudo nsenter -t "$pid" -m -p -u -n sh
```

A:

- `sudo`: needed because entering another process's namespaces usually requires elevated privileges
- `nsenter`: run a program inside namespaces of an existing process
- `-t "$pid"`: target process PID
- `-m`: enter mount namespace
- `-p`: enter PID namespace
- `-u`: enter UTS namespace
- `-n`: enter network namespace
- `sh`: start a shell after entering those namespaces

Practical meaning:

"Start a shell that sees the system the way that target process sees it for those namespace types."

### Q: If I pass only some flags to `nsenter`, what happens?

A: You enter only those namespaces.

Everything else stays in your current namespace context.

Example:

```bash
sudo nsenter -t <pid> -u sh
```

This changes hostname view only. Filesystem, process list, and network stay in the host view unless you also include `-m`, `-p`, or `-n`.

### Q: What other namespace flags can `nsenter` use?

A: Common namespace flags are:

- `-m`: mount namespace
- `-p`: PID namespace
- `-u`: UTS namespace
- `-n`: network namespace
- `-i`: IPC namespace
- `-U`: user namespace
- `-C`: cgroup namespace
- `-T`: time namespace

Useful non-namespace flags include:

- `-t <pid>`: target process
- `-a`: enter all namespaces available from the target

## Bind Mounts, Logs, and Host Access

### Q: Can a normal container mount a host directory?

A: Yes. That is very common and does not require a privileged container.

Example:

```bash
docker run -it --rm -v /home/laborant/repos:/data:rw busybox sh
```

This means:

- start a temporary interactive `busybox` container
- mount `/home/laborant/repos` from the host into `/data` inside the container
- allow read-write access

### Q: What is the practical effect of a bind mount like `/home/laborant/repos:/data:rw`?

A: Files under `/data` inside the container are the same files as `/home/laborant/repos` on the host.

So if the container writes to `/data/test.txt`, the host gets:

```bash
/home/laborant/repos/test.txt
```

### Q: Why are bind mounts common?

A: Common reasons include:

- development: mount source code into the container
- persistence: keep data outside the container lifecycle
- configuration: provide host-side config or certificates
- output sharing: collect reports, backups, or build artifacts on the host
- observability: let the container write logs to host storage

### Q: Are host-mounted log directories used for observability?

A: Yes. That is a common pattern, especially for applications that write logs to files.

Example:

```bash
docker run -d -v /var/log/myapp:/app/logs myapp
```

Then:

- the app writes to `/app/logs` inside the container
- the files are really stored at `/var/log/myapp` on the host
- host-side tools or log shippers can collect them later

### Q: Is writing logs to files the only common container logging pattern?

A: No. In modern container platforms, the preferred pattern is often to log to `stdout` and `stderr`.

Then the container runtime captures those streams directly.

### Q: What do `stdout` and `stderr` mean?

A:

- `stdout` = standard output, for normal program output
- `stderr` = standard error, for error messages and diagnostics

Container platforms commonly collect both streams automatically.

## Privileged Containers

### Q: What is a privileged container?

A: A privileged container is a container started with very broad access to the host, usually with:

```bash
docker run --privileged ...
```

Practical meaning:

- it gets almost all Linux capabilities
- it gets broad device access
- several normal security restrictions are relaxed

### Q: What can a privileged container often do that a normal container cannot?

A: Typical examples include:

- mount filesystems
- perform lower-level network administration
- access more devices under `/dev`
- change settings that require stronger capabilities

A simple demo inside a privileged container is:

```bash
mkdir -p /tmp/mnt-demo
mount -t tmpfs tmpfs /tmp/mnt-demo
mount | grep /tmp/mnt-demo
```

That often works in a privileged container and fails with `permission denied` in a normal container.

### Q: Can a privileged container affect the host?

A: Potentially yes.

Important distinction:

- namespaces may still isolate some views such as hostname, mounts, or PIDs
- but the kernel is shared with the host
- broad capabilities and device access can reduce isolation significantly

Examples of host risk include:

- modifying host files through bind mounts
- affecting host networking in some setups
- using exposed devices
- controlling the Docker daemon if its socket is mounted into the container

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
