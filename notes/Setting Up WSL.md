---
tags: [System Administration/Bash]
title: Setting Up WSL
created: '2022-07-03T23:32:54.737Z'
modified: '2022-07-03T23:56:45.425Z'
---

# Setting Up WSL

Pass through proxy env vars:
```powershell
❯ $env:WSLENV
HTTP_PROXY/u:HTTPS_PROXY/u:NO_PROXY/u
```
----

Set up DNS:
```bash
$ cat /etc/wsl.conf
[automount]
mountFsTab = true

[network]
generateResolvConf = false
```
```bash
$ rm -f /etc/resolv.conf
```
```bash
$ cat /etc/resolv.conf
search clients.asia-pac.shell.com
nameserver 134.162.23.1
nameserver 134.162.23.2
```
Workaround bug where `resolv.conf` gets nuked:
```bash
sudo chattr +i /etc/resolv.conf
```
* https://github.com/microsoft/WSL/issues/6977

----

Install certs in WSL:
```bash
sudo cp shell_pki.crt /usr/local/share/ca-certificates/shell_pki.crt
sudo chmod 644 /usr/local/share/ca-certificates/shell_pki.crt​
sudo update-ca-certificates
```
* https://eu001-sp.shell.com/sites/AAAAB1732/Pages/Configure-Linux-eg-WSL-or-Docker-to-work-via-ZScaler.aspx


```bash
$ cat /etc/profile.d/02-shared-root.sh
wsl.exe -u root -e mount --make-rshared /
```

```bash
$ cat /etc/profile.d/05-ssl-cert-file.sh
export SSL_CERT_FILE='/etc/ssl/certs/ca-certificates.crt'
```

----

Configure `mamba`

Ensure the base env is always on the path:
```bash
$ cat /etc/profile.d/09-conda-base.sh
export PATH=/opt/mambaforge/envs/base/bin:$PATH
```

Add `condabin` to the `sudo` `secure_path`:
```bash
sudo visudo
```
```
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin:/opt/mambaforge/envs/base/condabin"
```

Configure `ssl_verify` in the `.condarc`:
```yaml
ssl_verify: /etc/ssl/certs/ca-certificates.crt
```

Configure shared CNI directory for podman
```bash
sudo mkdir /opt/mambaforge/envs/base/etc/cni  
chown -R $(id -u):$(id -g) /opt/mambaforge/envs/base/etc/cni/
```

Use `tmpfs` for `/tmp`:
```bash
$ cat /etc/fstab
LABEL=cloudimg-rootfs   /        ext4   discard,errors=remount-ro         0 1
tmpfs                   /tmp     tmpfs  rw,nosuid,nodev,noatime,mode=1777 0 0
```

