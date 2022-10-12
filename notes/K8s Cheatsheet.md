---
favorited: true
tags: [Kubernetes]
title: K8s Cheatsheet
created: '2022-01-18T11:18:41.262Z'
modified: '2022-10-12T02:33:16.046Z'
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

Copying files to a File Share
```powershell
$rgp='<resource-group-name>'
$sta = '<storage-account-name>'
$share = '<file-share-name>'

$key = $(az storage account keys list -g $rgp -n $sta | ConvertFrom-Json)[0].value
$sas = $(az storage share generate-sas --account-key $key --account-name $sta --expiry '2023-01-01T00:00:00Z' --name $share --permissions 'dlrw').Trim('"')

# https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-files
$src_dir = 'test'
azcopy copy $src_dir "https://${sta}.file.core.windows.net/${share}/${src_dir}?${sas}" --recursive --log-level 'ERROR'

azcopy jobs clean
```
