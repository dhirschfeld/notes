---
tags: [Development/GitHub/Actions]
title: Specify run-name
created: '2023-05-10T04:14:38.015Z'
modified: '2023-05-10T04:14:50.449Z'
---

# Specify `run-name`

```yaml
run-name: ${{
    format(
      '[{0}] Build Packages',
      (github.event_name == 'pull_request' && format('pr/{0}', github.event.number)) ||
      (github.event_name == 'push' && github.ref_name) ||
      (github.event_name == 'release' && github.event.release.tag_name) ||
       github.event_name
    )
  }}
```
