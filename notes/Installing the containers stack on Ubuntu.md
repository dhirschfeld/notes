---
tags: [Containers]
title: Installing the containers stack on Ubuntu
created: '2021-11-15T03:04:11.899Z'
modified: '2022-05-11T23:55:37.128Z'
---

# Installing the `containers` stack on Ubuntu


> CAUTION: On Ubuntu 20.10 and newer, we highly recommend you use Buildah, Podman and Skopeo ONLY from EITHER the Kubic repo OR the official Ubuntu repos. Mixing and matching may lead to unpredictable situations including installation conflicts.

```bash
echo 'deb http://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/testing/xUbuntu_21.10/ /' | sudo tee /etc/apt/sources.list.d/devel:kubic:libcontainers:testing.list
curl -fsSL https://download.opensuse.org/repositories/devel:kubic:libcontainers:testing/xUbuntu_21.10/Release.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/devel_kubic_libcontainers_testing.gpg > /dev/null
sudo apt update
sudo apt install podman
```

* https://software.opensuse.org/download.html?project=devel%3Akubic%3Alibcontainers%3Atesting&package=podman
