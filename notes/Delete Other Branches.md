---
tags: [Development/Git]
title: Delete Other Branches
created: '2021-09-28T11:42:42.756Z'
modified: '2021-09-28T11:43:08.818Z'
---

# Delete Other Branches

```powershell
git branch | %{ $_.Trim() } | ?{ !$_.StartsWith('*') } | %{ git branch -D $_ }
```

