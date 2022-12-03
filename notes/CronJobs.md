---
tags: [Kubernetes]
title: CronJobs
created: '2022-11-04T03:27:59.814Z'
modified: '2022-12-01T04:17:05.433Z'
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
      backoffLimit: 6
      ttlSecondsAfterFinished: {{ mul 60 60 24 3 }}
      template:
        spec:
          enableServiceLinks: False
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

