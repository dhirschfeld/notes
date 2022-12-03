---
favorited: true
tags: [Kubernetes]
title: K8s Cheatsheet
created: '2022-01-18T11:18:41.262Z'
modified: '2022-11-16T03:21:35.337Z'
---

# K8s Cheatsheet

Sort by age:
```bash
kubectl get pods -A --sort-by=.metadata.creationTimestamp
```

Show Containers:
```bash
kubectl get pods -A -o=custom-columns=NameSpace:.metadata.namespace,POD:.metadata.name,CONTAINER:.spec.containers[*].image
```

Delete ~everything
```bash
kubectl -n test delete all --all   
```

Run a pod with an `imagePullSecret`
```bash
kubectl run -it --rm --image <registry>/ubuntu:22.04 --overrides='{"spec": {"imagePullSecrets": [{"name": "<secret-name>"}]}}' test-01 -- /bin/bash
```

Run debug pods from `mcr.microsoft.com`:
```
kubectl run -it --rm --image mcr.microsoft.com/azure-cli:latest debug-01 -- /bin/bash
```
```
kubectl run -it --rm --image mcr.microsoft.com/oss/mirror/docker.io/library/ubuntu:20.04 debug-01 -- /bin/bash
```

#### AKS Cluster Identities
```
az aks show -n "${cluster}" -g "${resource_group}" --query "identity"
az aks show -n "${cluster}" -g "${resource_group}" --query "identityProfile"
```

#### Apply HEREDOC

```bash
cat <<EOF | kubectl apply -f -
<YAML>
EOF
```
