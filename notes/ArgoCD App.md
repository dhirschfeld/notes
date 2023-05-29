---
tags: [Terraform]
title: ArgoCD App
created: '2023-05-29T01:27:04.653Z'
modified: '2023-05-29T01:27:50.688Z'
---

# ArgoCD App

```hcl
terraform {
  required_providers {
    kubernetes = {
      source  = "hashicorp/kubernetes"
    }
    helm = {
      source  = "hashicorp/helm"
    }
  }
}


locals {
  parameters = [
    for key, value in merge(
      {"namespace": var.argocd_project},
      var.parameters
    ):
    {"name" = key, "value" = value}
  ]
}
```
```hcl 
variable "application_name" {
  description = "The name of the ArgoCD Application."
  type        = string
}

variable "argocd_project" {
  description = "The ArgoCD Project (and k8s namespace) to deploy to."
  type        = string
}

variable "source_repo" {
  description = <<-EOF
    Either the Helm Repository containing the published Chart
    or the GitHub repository containing the source code for the Helm Chart.
  EOF
  type        = string
}

variable "source_path" {
  description = <<-EOF
    The path in the repository where the chart_name for the Helm Chart can be found.
    This is mutually exclusive with `source_path`. Do not use for Helm repositories!
  EOF
  type    = string
  default = null
}

variable "chart_name" {
  description = <<-EOF
    The name of the chart to deploy, if deploying from a Helm repository.
    This is mutually exclusive with `source_path`. Do not use for git hosted charts!
  EOF
  type    = string
  default = null
}

variable "parameters" {
  description = "Parameter overrides to pass to the Helm Chart."
  type        = map
  default     = {}
}

variable "value_files" {
  description = "The filepaths (relative to the source path) of other values files to include."
  type        = list(string)
  default     = null
}

variable "force_conflicts" {
  description = "Whether or not to override existing parameters."
  type        = bool
  default     = true
}

variable "target_revision" {
  description = "To specify the tag/branch/HEAD/commit ArgoCD should track."
  type = string
  default = "HEAD"
}

```
```hcl
# https://registry.terraform.io/providers/hashicorp/kubernetes/latest/docs/resources/manifest
resource "kubernetes_manifest" "argocd_app" {
  # https://github.com/argoproj/argo-cd/blob/master/docs/operator-manual/application.yaml
  manifest = {
    "apiVersion" = "argoproj.io/v1alpha1"
    "kind"       = "Application"
    "metadata" = {
      "name"      = var.application_name
      "namespace" = "argocd"
    }
    "spec" = {
      "project" = var.argocd_project
      "source"  = {
        "repoURL"        = var.source_repo
        "path"           = var.source_path
        "chart"          = var.chart_name
        "targetRevision" = var.target_revision
        "helm" = {
          "parameters" = local.parameters
          "valueFiles" = var.value_files == null ? ["values.yaml"] : var.value_files
        }
      }
      "destination" = {
        "server"    = "https://kubernetes.default.svc"
        "namespace" = var.argocd_project
      }
      "syncPolicy" = {
        "automated" = {
          "prune"    = true
          "selfHeal" = true
        }
        "syncOptions" = [
          "PruneLast=true",
          "CreateNamespace=true",
        ]
      }
    }
  }
  field_manager {
    force_conflicts = var.force_conflicts
  }
  computed_fields = [
    "metadata.labels",
    "metadata.annotations",
    "spec.source.targetRevision",
    "spec.source.helm.parameters",
  ]
}
```
