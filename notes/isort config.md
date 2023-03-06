---
tags: [Python/Packaging]
title: isort config
created: '2023-02-17T01:16:12.926Z'
modified: '2023-02-17T01:17:22.175Z'
---

# `isort` config

```toml
[tool.isort]
profile = "black"
line_length = 90
force_grid_wrap = 2
multi_line_output=3
include_trailing_comma = true
lines_before_imports = 0
lines_after_imports = 2
force_alphabetical_sort_within_sections = true
sections = [
  "FUTURE",
  "STDLIB",
  "THIRDPARTY",
  "FIRSTPARTY",
  "LOCALFOLDER",
]
default_section = "THIRDPARTY"
known_first_party = ["eq"]
```

