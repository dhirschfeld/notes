---
tags: [Containers]
title: Mount a git submodule
created: '2023-01-05T03:39:03.153Z'
modified: '2023-01-05T03:39:23.989Z'
---

# Mount a git submodule

```
# Install MSODBC
RUN --mount=type=bind,source=./bootstrap/ubuntu,target=/tmp/bootstrap /tmp/bootstrap/msodbc/install.sh --version '18.1.2.1-1'

# Install Azure CLI
RUN --mount=type=bind,source=./bootstrap/ubuntu,target=/tmp/bootstrap /tmp/bootstrap/azure-cli/install.sh --version '2.43.0-1'
```

