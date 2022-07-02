---
tags: [Python]
title: RStudio Install
created: '2021-05-31T00:21:51.668Z'
modified: '2021-07-08T10:51:55.763Z'
---

# RStudio Install

* https://github.com/rocker-org/rocker-versioned2/blob/master/scripts/install_rstudio.sh

```bash
version='1.4.1106'
filename="rstudio-server-${version}-amd64.deb"
codename=$(lsb_release -cs)
codename='bionic'
url="https://s3.amazonaws.com/rstudio-ide-build/server/${codename}/amd64/${filename}"
curl -sSLo $filename $url

apt update
apt install libclang-dev libpq5

dpkg -i $filename
rm -f $filename

# https://github.com/rocker-org/rocker-versioned2/issues/137
rm -f /var/lib/rstudio-server/secure-cookie-key

## RStudio wants an /etc/R, will populate from $R_HOME/etc
mkdir -p /etc/R

R_BIN=$(which R)
echo "rsession-which-r=${R_BIN}" > /etc/rstudio/rserver.conf
echo "auth-none=1" >> /etc/rstudio/rserver.conf

## use more robust file locking to avoid errors when using shared volumes:
echo "lock-type=advisory" > /etc/rstudio/file-locks

# Log to stderr
LOGGING="[*]
log-level=warn
logger-type=stderr
"
printf "%s" "$LOGGING" > /etc/rstudio/logging.conf

chown -Rv 1000:1000 /var/lib/rstudio-server
chmod -Rv g=u /var/lib/rstudio-server

chown -Rv 1000:1000 /etc/rstudio
chmod -Rv g=u /etc/rstudio
```
