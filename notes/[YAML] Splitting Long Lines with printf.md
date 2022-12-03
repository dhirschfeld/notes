---
tags: [Kubernetes]
title: '[YAML] Splitting Long Lines with printf'
created: '2022-12-01T03:34:00.321Z'
modified: '2022-12-01T03:36:15.373Z'
---

# [`YAML`] Splitting Long Lines with `printf`

```yaml
      spec:
        enableServiceLinks: False
        containers:
        - name: "{{ .Chart.Name }}"
          image: {{ printf "%s/%s:%s"
            .Values.image.registry
            .Values.image.name
            .Values.image.tag
          }}
```
