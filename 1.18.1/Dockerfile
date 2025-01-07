FROM hexpm/elixir:1.18.1-erlang-27.2-ubuntu-noble-20241118.1

ENV NODE_VERSION="20.12.2"
ENV NODE_DOWNLOAD_URL="https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.xz"

RUN set -xe \
  && apt-get update \
  && apt-get install -y ca-certificates \
  && apt-get install -y git curl xz-utils make cmake g++ \
  && curl -fSL -o node-dist.tar.xz $NODE_DOWNLOAD_URL \
	&& tar -xJf node-dist.tar.xz -C /usr/local --strip-components=1 \
	&& rm node-dist.tar.xz \
  && ln -s /usr/local/bin/node /usr/local/bin/nodejs

RUN <<EOF
  set -xe
  apt-get update

  # Needs to run separately to build on M2/M3 Macs with Rosetta for some reason
  # Ref: https://github.com/docker/for-mac/issues/7255#issuecomment-2540082464
  apt-get install -y --no-install-recommends ca-certificates

  # Install git so CI can clone the repository
  apt-get install -y --no-install-recommends git

  # Install curl and xz-utils to download and unpack the NodeJS binaries
  apt-get install -y --no-install-recommends curl xz-utils

  # Dependencies for Elixir to compile binaries
  apt-get install -y --no-install-recommends make cmake g++

  # Install NodeJS binary
  curl -fSL -o node-dist.tar.xz $NODE_DOWNLOAD_URL
  tar -xJf node-dist.tar.xz -C /usr/local --strip-components=1 
  rm node-dist.tar.xz
  ln -sf /usr/local/bin/node /usr/local/bin/nodejs
EOF
