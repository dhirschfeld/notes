---
tags: [Azure/Storage]
title: Injecting Storage Credentials with Terraform
created: '2023-01-09T01:57:00.928Z'
modified: '2023-01-09T01:57:52.261Z'
---

# Injecting Storage Credentials with Terraform

```
# https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/secret
resource "kubernetes_secret" "storage_creds" {
  metadata {
    name = "storage-creds"
    namespace = var.namespace
  }
  data = {
    azurestorageaccountname = var.storage_account.name
    azurestorageaccountkey  = var.storage_account.access_key
  }
  type = "Opaque"
}
```
