---
tags: [Azure]
title: AD Permission IDs
created: '2022-12-03T03:45:04.451Z'
modified: '2022-12-03T03:45:21.000Z'
---

# AD Permission IDs

```hcl
locals {
  resource_ids = {
    ms_graph        = "00000003-0000-0000-c000-000000000000"
    azure_storage   = "e406a681-f3d4-42a8-90b6-c2b029497af1"
    azure_data_lake = "e9f49c6b-5ce5-44c8-925d-015017e9f7ad"
    azure_key_vault = "cfa8b339-82a2-471a-a3c9-0fc0be7a4093"
    oss_database    = "123cd850-d9df-40bd-94d5-c9f07b7fa203"
    sql_database    = "022907d3-0f1b-48f7-badc-1ba6abab6d66"
  }

  roles = {
    ms_graph = {
      "user.export"            = "405a51b5-8d8d-430b-9842-8be4b0e9f324"
      "user.invite"            = "09850681-111b-4a89-9bed-3f2cae46d706"
      "user.manage_identities" = "c529cfca-c91b-489c-af2b-d92990b66ce6"
      "user.read_all"          = "df021288-bdef-4463-88db-98f22de89214"
      "user.read_write_all"    = "741f803b-c850-494e-b5df-cde7c675a1ca"
    }
  }

  # https://docs.microsoft.com/en-us/graph/permissions-reference
  # $appRoles = $(az ad sp list --display-name "Microsoft Graph" | ConvertFrom-Json).appRoles
  # $permissions = $(az ad sp list --display-name "Microsoft Graph" | ConvertFrom-Json).oauth2Permissions
  permissions = {
    ms_graph = {
      "email"     = "64a6cdd6-aab1-4aaf-94b8-3cc8405e90d0"
      "profile"   = "14dad69e-099b-42c9-810b-d002981feec1"
      "user.read" = "e1fe6dd8-ba31-4d61-89e7-88639da4683d"
    }
    # Get-AzADServicePrincipal | Where-Object {$_.DisplayName -eq "Azure Data Lake"}
    azure_storage = {
      "user_impersonate" ="03e0da56-190b-40ad-a80c-ea378c433f7f"
    }
    azure_data_lake = {
      "user_impersonate" = "9f15d22d-3cdf-430f-ba48-f75401c0408e"
    }
    azure_key_vault = {
      "user_impersonate" = "f53da476-18e3-4152-8e01-aec403e6edc0"
    }
    oss_database = {
      "user_impersonate" = "cef99a3a-4cd3-4408-8143-4375d1e38a17"
    }
    sql_database = {
      "user_impersonate" = "c39ef2d1-04ce-46dc-8b5f-e9a5c60f0fc9"
    }
  }

}
```

