---
tags: [Python]
title: RStudio
created: '2021-06-18T22:22:12.404Z'
modified: '2021-07-08T10:49:51.483Z'
---

# RStudio

* https://github.com/jupyterhub/jupyter-rsession-proxy/issues/93#issuecomment-864113051
```docker
RUN echo "auth-revocation-list-dir=/tmp/rstudio-server-revocation-list/" >> /etc/rstudio/rserver.conf
```

`master` required:
* https://github.com/jupyterhub/jupyter-rsession-proxy/issues/100



