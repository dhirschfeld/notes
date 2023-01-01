---
tags: [Kubernetes/Storage]
title: Mount SMB Share
created: '2022-12-06T02:01:19.001Z'
modified: '2022-12-06T02:02:18.124Z'
---

# Mount SMB Share

May require `SYS_ADMIN` / `DAC_READ_SEARCH` capabilities?

Doesn't work / notes:
```
cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Pod
metadata:
 name: test01
spec:
 containers:
   - name: test01
     image: "seaupowerteamuat.azurecr.io/seau_tns_containers/seau-debug:0.5.0"
     command:
       - /bin/bash
     securityContext:
       capabilities:
         add:
           - SYS_ADMIN
           - DAC_READ_SEARCH
EOF
```
