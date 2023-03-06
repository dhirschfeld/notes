---
tags: [Python/JupyterLab]
title: QuantDev Container
created: '2023-03-06T01:18:44.471Z'
modified: '2023-03-06T01:19:08.347Z'
---

# QuantDev Container

```dockerfile
# syntax=docker/dockerfile:1.4

# skopeo inspect docker://ghcr.io/sede-x/seau_tns_mambabuild/mambabuild:0.8.1 | jq '.Digest'
ARG BASE_IMAGE=ghcr.io/sede-x/seau_tns_mambabuild/mambabuild
ARG BASE_TAG=0.8.1
ARG BASE_DIGEST=sha256:aecb9e850329e2f04432191abc2e58bd54bb4fac12db8c3e4bc2f0e85358947a

ARG IMAGE_DESCRIPTION="A kitchen-sink Python analytics environment."


FROM $BASE_IMAGE:$BASE_TAG@$BASE_DIGEST as builder


ARG IMAGE_NAME

SHELL ["/bin/bash", "-eo", "pipefail", "-c"]

COPY ./local-pkgs/ /tmp/local-pkgs/

ARG IMAGE_VERSION

USER root

RUN micromamba info
RUN mamba create -n quantdev --clone build --copy
RUN micromamba install -n quantdev \
      -c  file:///tmp/local-pkgs \
      --always-copy --yes \
      python=3.10 quantdev="${IMAGE_VERSION//-/+}"

ENV MAMBA_DEFAULT_ENV=$IMAGE_NAME

RUN <<EOF
jupyter labextension install --no-build @finos/perspective-jupyterlab
jupyter lab build
jupyter lab clean -y
EOF

# Configure jupyterlab
# https://jupyterlab.readthedocs.io/en/stable/user/directories.html#overrides-json
RUN <<EOF
config_dir='/opt/mambaforge/envs/quantdev/etc/jupyter'
mkdir -p "${config_dir}"

cat << 'EOF1' > "${config_dir}/jupyter_server_config.json"
{
  "@jupyterlab/apputils-extension:themes": {
    "theme": "Darcula"
  },
  "@jupyterlab/terminal-extension:plugin": {
    "fontFamily": "FiraCode NF"
  }
}
EOF1

settings_dir='/opt/mambaforge/envs/quantdev/share/jupyter/lab/settings'
mkdir -p "${settings_dir}"

cat << 'EOF1' > "${settings_dir}/overrides.json"
{
  "@jupyterlab/apputils-extension:themes": {
    "theme": "Darcula"
  },
  "@jupyterlab/terminal-extension:plugin": {
    "fontFamily": "FiraCode NF"
  }
}
EOF1


EOF


# https://github.com/moby/buildkit/releases/download/v0.10.6/buildkit-v0.10.6.linux-amd64.tar.gz

###############################################################################

FROM $BASE_IMAGE:$BASE_TAG@$BASE_DIGEST

ARG BASE_IMAGE
ARG BASE_DIGEST

ARG IMAGE_REPO
ARG IMAGE_NAME
ARG IMAGE_VERSION
ARG IMAGE_DESCRIPTION


USER root


# Copy quantdev environment
COPY --from=builder --link /opt/mambaforge/envs/$IMAGE_NAME /opt/mambaforge/envs/$IMAGE_NAME

ENV MAMBA_DEFAULT_ENV=$IMAGE_NAME
ENV SHELL="/bin/bash"


# Allow user to sudo
RUN echo 'user ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers


# Install FiraCode Nerd Font
RUN <<EOF
mkdir -p /usr/share/fonts/truetype/firacode
curl -fsSL https://github.com/ryanoasis/nerd-fonts/releases/download/v2.2.2/FiraCode.zip -o ~/FiraCode.zip
unzip ~/FiraCode.zip -d /usr/share/fonts/truetype/firacode/
find /usr/share/fonts/truetype/firacode/ -type f -name '*Windows*' -delete
find /usr/share/fonts/truetype/firacode/ -type f -name '*otf' -delete
fc-cache -fv
chown -Rv user:user /usr/share/fonts/truetype/firacode
rm -f ~/FiraCode.zip
EOF


USER user

# RUN gh extension install cli/gh-webhook

# Create starship config
COPY --chown=user:user <<EOF /home/user/.config/starship.toml
command_timeout = 1000

[conda]
  symbol = " "

[python]
  disabled = true

[container]
  disabled=true

[directory]
  use_os_path_sep = false
  truncation_length = 8
  truncation_symbol = "…/"
EOF

RUN <<EOF
echo 'eval "$(starship init bash)"' >> /home/user/.bashrc
echo 'source <(kubectl completion bash)' >> /home/user/.bashrc

echo 'alias cls="clear"' >> /home/user/.bash_aliases
echo 'alias la="exa -lah"' >> /home/user/.bash_aliases
EOF


# https://github.com/opencontainers/image-spec/blob/main/annotations.md#pre-defined-annotation-keys
LABEL org.opencontainers.image.base.name=$BASE_IMAGE \
      org.opencontainers.image.base.digest=$BASE_DIGEST \
      org.opencontainers.image.description=$IMAGE_DESCRIPTION

ENV IMAGE_VERSION="${IMAGE_REPO}/${IMAGE_NAME}:${IMAGE_VERSION}"
```
