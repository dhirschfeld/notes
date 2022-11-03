---
tags: [Kubernetes, Kubernetes/Helm]
title: Finding out which images a Helm Chart uses
created: '2022-10-19T02:56:19.671Z'
modified: '2022-10-19T02:57:22.647Z'
---

# Finding out which images a Helm Chart uses


```
helm template .     | yq -s '[..|.image? | select(.)] | unique'
```
