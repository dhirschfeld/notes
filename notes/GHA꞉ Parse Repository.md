---
tags: [Development/GitHub/Actions]
title: 'GHA: Parse Repository'
created: '2022-09-05T12:18:29.746Z'
modified: '2022-09-05T12:19:41.926Z'
---

# GHA: Parse Repository

```yaml
name: Parse Repository
description: "Returns the organization and repository names from the '{org}/{repo}' input."
inputs:
  repository:
    required: true
    type: string
    description: "The fully-qualified '{org}/{repo}' name."
outputs:
  org:
    description: "The GitHub organization name."
    value: ${{ steps.parse_repo.outputs.org }}
  repo:
    description: "The GitHub repository name."
    value: ${{ steps.parse_repo.outputs.repo }}
runs:
  using: "composite"
  steps:
    - id: parse_repo
      shell: bash
      run: |
        set -euox pipefail
        IFS='/' read owner repo <<< ${{ inputs.repo }}
        echo "::set-output name=org::${owner}"
        echo "::set-output name=repo::${repo}

```
