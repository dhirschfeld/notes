---
tags: [Development/Git]
title: Rebasing
created: '2022-11-10T01:52:31.325Z'
modified: '2022-11-19T23:04:03.002Z'
---

# Rebasing

### Rebasing a Squashed Branch

```bash
git switch main
git pull
git switch feature-branch
git rebase --onto main feature-branch^ 
```

* https://womanonrails.com/git-rebase-onto

### Rebasing but Keeping all Changes

Keep current branch:
```bash
git rebase -X theirs main
```


