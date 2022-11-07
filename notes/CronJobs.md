---
tags: [Kubernetes]
title: CronJobs
created: '2022-11-04T03:27:59.814Z'
modified: '2022-11-04T03:28:54.390Z'
---

# CronJobs

```bash
❯ cat <<'EOF' | kubectl apply -f -
apiVersion: batch/v1
kind: CronJob
metadata:
  name: dave-test
spec:
  schedule: "0 0 * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: azure-cli
            image: mcr.microsoft.com/azure-cli:latest
            imagePullPolicy: Always
            command:
            - /bin/bash
            - -c
            - |
              set -euxo pipefail
              echo "Hello World!"
          restartPolicy: OnFailure
EOF
```
```bash
kubectl create job --from=cronjob/dave-test test-cron-job-01
```

