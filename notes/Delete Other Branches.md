---
tags: [Development/Git]
title: Delete Other Branches
created: '2021-09-28T11:42:42.756Z'
modified: '2022-09-26T02:46:55.934Z'
---

# Delete Other Branches

```powershell
git branch | %{ $_.Trim() } | ?{ !$_.StartsWith('*') -and $_ -ne 'main' } | %{ git branch -D $_ }
```

```bash
git branch | grep -vE "^(\*|main)" | xargs git branch -D
```

