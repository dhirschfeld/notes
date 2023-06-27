---
tags: [Kubernetes]
title: CronJobs
created: '2022-11-04T03:27:59.814Z'
modified: '2023-06-27T03:44:53.426Z'
---

# CronJobs

```bash
❯ cat <<'EOF' | kubectl apply -f -
# kubectl create job --from=cronjob/dave-test test-cron-job-01
# https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.26/#cronjob-v1-batch
apiVersion: batch/v1
kind: CronJob
metadata:
  name: "{{ .Chart.Name }}"
  namespace: "{{ .Values.namespace }}"
spec:
  schedule: "{{ .Values.cronjob.schedule }}"
  timeZone: Australia/Queensland
  failedJobsHistoryLimit: 99
  jobTemplate:
    spec:
      backoffLimit: 0
      ttlSecondsAfterFinished: {{ .Values.cronjob.ttlSecondsAfterFinished }}
      template:
        spec:
          restartPolicy: Never
          enableServiceLinks: False
          containers:
            - name: "{{ .Chart.Name }}"
              image: {{ printf "%s/%s:%s"
                .Values.container.image.registry
                .Values.container.image.name
                .Values.container.image.tag
              }}
              imagePullPolicy: "{{ .Values.container.image.pullPolicy }}"
              env:
                - name: APP_DEBUG
                  value: "{{ .Values.debug }}"
              envFrom:
                - secretRef:
                    name: my-secret
              command:
              - /bin/bash
              - -c
              - {{ .Values.cronjob.command }}
EOF
```
```bash
kubectl create job --from=cronjob/dave-test test-cron-job-01
```

