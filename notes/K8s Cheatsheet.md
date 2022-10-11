---
favorited: true
tags: [Kubernetes]
title: K8s Cheatsheet
created: '2022-01-18T11:18:41.262Z'
modified: '2022-10-02T05:51:39.253Z'
---

# K8s Cheatsheet

Sort by age:
```bash
kubectl get pods -A --sort-by=.metadata.creationTimestamp
```

Show Containers:
```bash
kubectl get pods -A -o=custom-columns=NameSpace:.metadata.namespace,POD:.metadata.name,CONTAINER:.spec.containers[*].name
```

Delete ~everything
```bash
kubectl -n test delete all --all   
```

Run a pod with an `imagePullSecret`
```bash
kubectl run -it --rm --image <registry>/ubuntu:22.04 --overrides='{"spec": {"imagePullSecrets": [{"name": "<secret-name>"}]}}' test-01 -- /bin/bash
```
