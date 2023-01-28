---
tags: [Kubernetes/Ingress]
title: Cipher Suites
created: '2023-01-20T10:30:02.203Z'
modified: '2023-01-20T10:34:56.017Z'
---

# Cipher Suites

* https://doc.traefik.io/traefik/middlewares/http/headers/
* https://doc.traefik.io/traefik/routing/providers/kubernetes-crd/#kind-tlsoption
* https://www.paulsblog.dev/harden-your-website-with-traefik-and-security-headers/
* https://www.thesslstore.com/blog/cipher-suites-algorithms-security-settings/


### 1.2
```
TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256
```

### 1.3
```
TLS_AES_256_GCM_SHA384
TLS_CHACHA20_POLY1305_SHA256
TLS_AES_128_GCM_SHA256
```
