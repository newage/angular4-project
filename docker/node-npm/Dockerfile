FROM debian:jessie

ENV NPM_CONFIG_CACHE=/var/www/.npm-cache
ENV NPM_PATH=/nodejs
ENV NODE_VERSION=v6.10.0

RUN apt-get update -y && apt-get install --no-install-recommends -y -q curl python build-essential git ca-certificates libfontconfig
RUN mkdir -p ${NPM_PATH} && curl http://nodejs.org/dist/${NODE_VERSION}/node-${NODE_VERSION}-linux-x64.tar.gz | tar xvzf - -C ${NPM_PATH} --strip-components=1

ENV PATH $PATH:${NPM_PATH}/bin
RUN npm install -g grunt-cli

RUN apt-get remove -y ca-certificates libfontconfig \
    && apt-get autoremove -y \
    && apt-get clean \
    && rm -r /var/lib/apt/lists/*

ARG PUID=
RUN usermod -u ${PUID} www-data

RUN mkdir -p ${NPM_CONFIG_CACHE} && chown -R www-data:www-data ${NPM_CONFIG_CACHE}
VOLUME ${NPM_CONFIG_CACHE}
ARG PROJECT_PATH=
WORKDIR ${PROJECT_PATH}
