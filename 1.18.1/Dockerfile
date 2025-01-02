FROM hexpm/elixir:1.18.1-erlang-27.2-ubuntu-noble-20241118.1

ENV NODE_VERSION="20.12.2"
ENV NODE_DOWNLOAD_URL="https://nodejs.org/dist/v${NODE_VERSION}/node-v${NODE_VERSION}-linux-x64.tar.xz"

RUN set -xe \
  && apt-get update \
  && apt-get install -y curl xz-utils imagemagick make cmake g++ \
  && curl -fSL -o node-dist.tar.xz $NODE_DOWNLOAD_URL \
	&& tar -xJf node-dist.tar.xz -C /usr/local --strip-components=1 \
	&& rm node-dist.tar.xz \
  && ln -s /usr/local/bin/node /usr/local/bin/nodejs
