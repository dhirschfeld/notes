---
favorited: true
tags: [Kubernetes]
title: K8s Secrets & Key Vaults
created: '2022-01-17T04:06:58.783Z'
modified: '2022-01-20T11:46:58.096Z'
---

# K8s Secrets & Key Vaults

Decode a secret
```bash
kubectl get secret/argocd-secret -n argocd -o json | jq '.data | map_values(@base64d)'
```

Importing a cert into Azure Key Vault:
```bash
az keyvault certificate import --file quantdev.pfx --name quantdev --password $password --vault-name smc-key-vault --subscription az-smc
```
* https://docs.microsoft.com/en-us/cli/azure/keyvault/certificate?view=azure-cli-latest#az_keyvault_certificate_import

Setting a Key Vault secret:
```bash
az keyvault secret set --vault-name 'smc-ae-kv-651fcd' --name "database--aemo" --file "~/.config/stanwell/database/aemo.json"
az keyvault secret set-attributes --vault-name 'smc-ae-kv-651fcd' --name "database--aemo" --content-type 'application/json'
```

```bash
> $sqlnet = "\\stanwell.com\cdshare\Corporate\Oracle\sqlnet.ora"
> $tnsnames = "\\stanwell.com\cdshare\Corporate\Oracle\tnsnames.ora"
> kubectl create secret generic -n trading oracle --from-file $sqlnet --from-file $tnsnames
> kubectl describe secret/oracle -n trading
Name:         oracle
Namespace:    trading
Labels:       <none>
Annotations:  <none>

Type:  Opaque

Data
====
sqlnet.ora:    493 bytes
tnsnames.ora:  39374 bytes
```

```powershell
$password = '********'
$payload = "{\`"username\`": \`"$env:USERNAME\`", \`"password\`": \`"$password\`"}"
$key_vault = 'smc-ae-kv-651fcd'
az keyvault secret set --vault-name $key_vault --name "argocd--ghe-creds" --value "$payload"
az keyvault secret set-attributes --vault-name $key_vault --name "argocd--ghe-creds" --content-type 'application/json'
```
