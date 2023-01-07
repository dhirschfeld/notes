---
tags: [Containers]
title: Cleanup after apt
created: '2023-01-05T03:37:46.044Z'
modified: '2023-01-05T03:38:55.959Z'
---

# Cleanup after `apt`

```dockerfile
RUN <<EOF
apt-get -qq -o Dpkg::Use-Pty=0 update --yes
apt-get -qq -o Dpkg::Use-Pty=0 install --yes nano

apt-get -qq clean
rm -rf /var/lib/apt/lists/*
rm -rf /var/cache/apt/archives/*
rm -rf /var/tmp/*
rm -rf --one-file-system /tmp/*
truncate -s 0 /var/log/*log
EOF
```
