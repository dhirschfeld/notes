---
tags: [Azure]
title: Copy a secret from one Key Vault to another
created: '2023-05-26T02:22:50.827Z'
modified: '2023-05-26T02:25:22.445Z'
---

# Copy a secret from one Key Vault to another

```bash
src='<src-key-vault>'
dst='<dst-key-vault>'
name='<name>'

value=$(echo $(az keyvault secret show --vault-name "${src}" --name "${name}" | jq -r '.value')
az keyvault secret set --vault-name "${dst}" --name "${name}" --value "${value}"
az keyvault secret set-attributes --vault-name "${dst}" --name "${name}" --content-type 'application/json'
```

