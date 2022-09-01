---
tags: [Azure/Storage, Terraform]
title: Provision FileShare Using azapi
created: '2022-09-01T03:02:34.443Z'
modified: '2022-09-01T03:03:57.065Z'
---

# Provision FileShare Using `azapi`

```terraform
# FIXME:
# `azurerm_storage_share` can't be used due to a bug in terraform:
# https://github.com/hashicorp/terraform-provider-azurerm/issues/2977

# # https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/storage_share
# resource "azurerm_storage_share" "share" {
#   for_each = toset(var.shares)
#   depends_on          = [
#     module.storage_account
#   ]
#   name                  ="${each.key}"
#   storage_account_name  = module.storage_account.name
#   access_tier           = "Premium"
#   quota                 = 100
# }

# https://docs.microsoft.com/en-us/azure/templates/microsoft.storage/storageaccounts/fileservices/shares?pivots=deployment-language-terraform
resource "azapi_resource" "share" {
  for_each = toset(var.shares)
  depends_on          = [
    module.storage_account
  ]
  name      = "${each.key}"
  parent_id = "${module.storage_account.id}/fileServices/default"
  type      = "Microsoft.Storage/storageAccounts/fileServices/shares@2021-09-01"
  body = jsonencode({
    properties = {
      accessTier = "Premium"
      shareQuota = 100

    }
  })
}
```
