---
tags: [Kubernetes]
title: Debugging with Ephemeral Containers
created: '2023-03-10T03:02:15.978Z'
modified: '2023-03-10T03:04:28.688Z'
---

# Debugging with Ephemeral Containers

```bash
kubectl -n <namespace> debug -it --image=<image_name>:<image_tag> --target=<container_name> <pod_name>
```

Might need `CAP_SYS_ADMIN`, `CAP_SYS_PTRACE`
* https://unofficial-kubernetes.readthedocs.io/en/latest/concepts/policy/container-capabilities/

