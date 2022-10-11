---
tags: [Kubernetes, Kubernetes/Authentication, Kubernetes/Traefik]
title: Traefik ForwardAuth with oauth2-proxy
created: '2022-09-18T23:56:01.077Z'
modified: '2022-09-19T01:02:50.745Z'
---

# Traefik ForwardAuth with `oauth2-proxy`

* https://github.com/oauth2-proxy/oauth2-proxy/issues/1768
* https://github.com/oauth2-proxy/oauth2-proxy/issues/1639#issuecomment-1224763241

> After successful authentication on the IdP and then redirected back to the Ingress resource, the user headers (X-Forwarded-User, X-Forwarded-Groups, X-Forwarded-Email and X-Forwarded-Preferred-Username) should be set by OAuth2 Proxy and sent to the upstream servers.

> The --pass-* options are for when oauth2-proxy is acting as a reverse proxy, and define headers that are added to the HTTP request that oauth2-proxy makes to the upstream. They do nothing when oauth2-proxy is operating in auth-request mode behind Traefik or nginx.
>
> The --set-* options are for the auth-request mode, and define headers that are added the the HTTP response that oauth2-proxy returns to Traefik when it calls /oauth2/auth. They do nothing when oauth2-proxy is acting as a reverse proxy.

* https://github.com/oauth2-proxy/oauth2-proxy/issues/1441#issuecomment-965510045
