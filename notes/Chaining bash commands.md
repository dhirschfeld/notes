---
tags: [System Administration/Linux]
title: Chaining bash commands
created: '2021-01-12T01:49:16.174Z'
modified: '2021-03-29T03:24:20.501Z'
---

# Chaining bash commands

```bash
A; B    # Run A and then B, regardless of success of A
A && B  # Run B if and only if A succeeded
A || B  # Run B if and only if A failed
A &     # Run A in background.
```

* https://askubuntu.com/a/539293

