---
tags: [Containers]
title: Running Moby BuildKit in a Container
created: '2023-06-15T01:52:40.717Z'
modified: '2023-06-15T11:51:19.200Z'
---

# Running Moby BuildKit in a Container

* https://docs.docker.com/build/buildkit/
* https://github.com/moby/buildkit#containerizing-buildkit

* https://github.com/moby/buildkit/blob/master/docs/rootless.md
* https://github.com/rootless-containers/rootlesskit
* https://github.com/moby/buildkit/tree/master/examples/kubernetes

* https://github.com/moby/buildkit/blob/master/examples/buildctl-daemonless/buildctl-daemonless.sh
----

To run the client and an ephemeral daemon in a single container ("daemonless mode"):

```
docker run \
    -it \
    --rm \
    --privileged \
    -v /path/to/dir:/tmp/work \
    --entrypoint buildctl-daemonless.sh \
    moby/buildkit:master \
        build \
        --frontend dockerfile.v0 \
        --local context=/tmp/work \
        --local dockerfile=/tmp/work
```
Rootless:
```
docker run \
    -it \
    --rm \
    --security-opt seccomp=unconfined \
    --security-opt apparmor=unconfined \
    -e BUILDKITD_FLAGS=--oci-worker-no-process-sandbox \
    -v /path/to/dir:/tmp/work \
    --entrypoint buildctl-daemonless.sh \
    moby/buildkit:master-rootless \
        build \
        --frontend \
        dockerfile.v0 \
        --local context=/tmp/work \
        --local dockerfile=/tmp/work
```

* https://github.com/containerd/nerdctl/blob/v1.0.0/docs/build.md#setting-up-buildkit-with-containerd-worker :star:
* https://github.com/moby/buildkit/issues/2193 :star:

```
buildctl \
  --addr kube-pod://podname?container=containername&namespace=nsname&context=ctxname \
  build --frontend dockerfile.v0 --local context=/path/to/dir --local dockerfile=/path/to/dir
```

```bash
echo FROM hello-world > Dockerfile
```

```
❯ ./buildkitd --help
NAME:
   buildkitd - build daemon

USAGE:
   buildkitd [global options] command [command options] [arguments...]

VERSION:
   v0.11.6

COMMANDS:
   help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --rootless                                  set all the default options to be compatible with rootless containers
   --config value                              path to config file (default: "/etc/buildkit/buildkitd.toml")
   --debug                                     enable debug output in logs
   --root value                                path to state directory (default: "/var/lib/buildkit")
   --addr value                                listening address (socket or tcp) (default: "unix:///run/buildkit/buildkitd.sock")
   --group value                               group (name or gid) which will own all Unix socket listening addresses
   --debugaddr value                           debugging address (eg. 0.0.0.0:6060)
   --tlscert value                             certificate file to use
   --tlskey value                              key file to use
   --tlscacert value                           ca certificate to verify clients
   --allow-insecure-entitlement value          allows insecure entitlements e.g. network.host, security.insecure
   --containerd-worker value                   enable containerd workers (true/false/auto) (default: "auto")
   --containerd-worker-addr value              containerd socket (default: "/run/containerd/containerd.sock")
   --containerd-worker-labels value            user-specific annotation labels (com.example.foo=bar)
   --containerd-worker-net value               worker network type (auto, cni or host) (default: "auto")
   --containerd-cni-config-path value          path of cni config file (default: "/etc/buildkit/cni.json")
   --containerd-cni-binary-dir value           path of cni binary files (default: "/opt/cni/bin")
   --containerd-cni-pool-size value            size of cni network namespace pool (default: 0)
   --containerd-worker-snapshotter value       snapshotter name to use (default: "overlayfs")
   --containerd-worker-apparmor-profile value  set the name of the apparmor profile applied to containers
   --containerd-worker-selinux                 apply SELinux labels
   --containerd-worker-rootless                enable rootless mode
   --containerd-worker-gc                      Enable automatic garbage collection on worker
   --containerd-worker-gc-keepstorage value    Amount of storage GC keep locally (MB) (default: 2000)
   --oci-worker value                          enable oci workers (true/false/auto) (default: "auto")
   --oci-worker-labels value                   user-specific annotation labels (com.example.foo=bar)
   --oci-worker-snapshotter value              name of snapshotter (overlayfs, native, etc.) (default: "auto")
   --oci-worker-proxy-snapshotter-path value   address of proxy snapshotter socket (do not include 'unix://' prefix)
   --oci-worker-platform value                 override supported platforms for worker
   --oci-worker-net value                      worker network type (auto, cni or host) (default: "auto")
   --oci-cni-config-path value                 path of cni config file (default: "/etc/buildkit/cni.json")
   --oci-cni-binary-dir value                  path of cni binary files (default: "/opt/cni/bin")
   --oci-cni-pool-size value                   size of cni network namespace pool (default: 0)
   --oci-worker-binary value                   name of specified oci worker binary
   --oci-worker-apparmor-profile value         set the name of the apparmor profile applied to containers
   --oci-worker-selinux                        apply SELinux labels
   --oci-worker-rootless                       enable rootless mode
   --oci-worker-no-process-sandbox             use the host PID namespace and procfs (WARNING: allows build containers to kill (and potentially ptrace) an arbitrary process in the host namespace)
   --oci-worker-gc                             Enable automatic garbage collection on worker
   --oci-worker-gc-keepstorage value           Amount of storage GC keep locally (MB) (default: 2000)
   --help, -h                                  show help
   --version, -v                               print the version
```
