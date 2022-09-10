---
tags: [Development/GitHub/Actions]
title: 'GHA: Showing Debug Info'
created: '2022-09-05T00:32:39.217Z'
modified: '2022-09-05T00:34:05.601Z'
---

# GHA: Showing Debug Info


```yaml
name: Show Debug Info

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

  workflow_dispatch:

jobs:
  debug:
    runs-on: ubuntu-latest
    steps:
      - name: Show Environment
        run: env | sort
      - name: Show GitHub Context
        env:
          GITHUB_CONTEXT: ${{ toJson(github) }}
        run: echo "$GITHUB_CONTEXT"
```
