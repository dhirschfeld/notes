---
tags: [Kubernetes/Storage]
title: AzCopy
created: '2022-11-07T04:07:22.667Z'
modified: '2022-11-07T04:08:04.566Z'
---

# AzCopy


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


