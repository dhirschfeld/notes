---
tags: [Terraform]
title: Creating an ImagePullSecret
created: '2022-09-13T01:31:04.037Z'
modified: '2022-09-13T01:32:37.767Z'
---

# Creating an `ImagePullSecret`

```hcl
locals {
  acr_username  = data.azurerm_container_registry.acr.admin_username
  acr_password  = data.azurerm_container_registry.acr.admin_password
  docker_config = jsonencode({
    auths = {
      "${data.azurerm_container_registry.acr.login_server}" = {
        "username" = local.acr_username
        "password" = local.acr_password
        "auth"     = base64encode("${local.acr_username}:${local.acr_password}")
      }
    }
  })
}

# https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/secret_v1
resource "kubernetes_secret_v1" "example" {
  metadata {
    name      = "var.acr_name"
    namespace = kubernetes_namespace.traefik.metadata[0].name
  }
  type = "kubernetes.io/dockerconfigjson"
  data = {
    ".dockerconfigjson" = local.docker_config
  }
}
```
