---
tags: [Kubernetes]
title: Theming ArgoCD
created: '2022-12-15T23:02:42.961Z'
modified: '2022-12-15T23:05:56.218Z'
---

# Theming ArgoCD

* https://argo-cd.readthedocs.io/en/stable/operator-manual/custom-styles/
* https://saumeya.github.io/4.custom-styles-argocd.html
* https://akuity.io/blog/how-to-create-a-theme-for-your-argocd-with-minimal-css/


```yaml
# https://github.com/argoproj/argo-helm/blob/main/charts/argo-cd/values.yaml
configs:
  cm:
    url: https://argocd.my-domain.com
    admin.enabled: true
    exec.enabled: true
    server.rbac.log.enforce.enable: true
    statusbadge.enabled: true

    # OIDC configuration as an alternative to dex (optional).
    # oidc.config: |
    #   name: AzureAD
    #   issuer: https://login.microsoftonline.com/TENANT_ID/v2.0
    #   clientID: CLIENT_ID
    #   clientSecret: $oidc.azuread.clientSecret
    #   rootCA: |
    #     -----BEGIN CERTIFICATE-----
    #     ... encoded certificate data here ...
    #     -----END CERTIFICATE-----
    #   requestedIDTokenClaims:
    #     groups:
    #       essential: true
    #   requestedScopes:
    #     - openid
    #     - profile
    #     - email

  params:
    # https://argo-cd.readthedocs.io/en/stable/operator-manual/ingress/#traefik-v22
    server.insecure: true

  styles: |
    .sidebar__logo img {
      content: url(https://my-logo);
    }

```
