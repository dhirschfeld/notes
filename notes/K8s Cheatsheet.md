---
favorited: true
tags: [Kubernetes]
title: K8s Cheatsheet
created: '2022-01-18T11:18:41.262Z'
modified: '2022-08-22T02:57:03.583Z'
---

# K8s Cheatsheet

Sort by age:
```
kubectl get pods -A --sort-by=.metadata.creationTimestamp
```

Show Containers:
```
kubectl get pods -A -o=custom-columns=NameSpace:.metadata.namespace,POD:.metadata.name,CONTAINER:.spec.containers[*].name
```
