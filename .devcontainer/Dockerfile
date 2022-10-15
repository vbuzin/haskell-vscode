# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.245.2/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version (use ubuntu-22.04 or ubuntu-18.04 on local arm64/Apple Silicon): ubuntu-22.04, ubuntu-20.04, ubuntu-18.04
ARG VARIANT="jammy"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends build-essential libgmp-dev

ARG GPG_KEY=7784930957807690A66EBDBE3786C5262ECB4A3F
RUN gpg --batch --keyserver keys.openpgp.org --recv-keys $GPG_KEY

RUN curl https://downloads.haskell.org/~ghcup/aarch64-linux-ghcup > /usr/bin/ghcup \
    && chmod +x /usr/bin/ghcup \
    && ghcup config set gpg-setting GPGStrict

RUN ghcup install cabal --isolate /usr/local/bin \
    && ghcup install ghc --force --isolate /usr/local \
    && ghcup install hls --force --isolate /usr/local