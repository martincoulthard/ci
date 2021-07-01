# syntax = docker/dockerfile:experimental
# Interim container so we can copy pulumi binaries
# Must be defined first
ARG PULUMI_VERSION=latest
ARG RUNTIME_VERSION=12.18.0
ARG PULUMI_IMAGE=pulumi/pulumi-base
FROM ${PULUMI_IMAGE}:${PULUMI_VERSION} as pulumi

FROM docker:18.09.7



RUN apk add --update \
    jq \
    git \
    zip \
    openssh \
    openssl \
    openssl-dev \
    libffi-dev \
    python \
    python-dev \
    python3-dev \
    py-pip \
    build-base \
    docker-compose \
    nodejs=10.19.0-r0 \
    npm=10.19.0-r0 \
    libc6-compat \
    ca-certificates \
    && pip install --upgrade --user \
    # docker-compose pulls die with paramiko 2.7.2:: AttributeError: type object 'EllipticCurvePublicKey' has no attribute 'from_encoded_point'
    paramiko==2.4.2 \ 
    awscli==1.16.193 \
    awsebcli==3.15.2 \
    cryptography==2.4.2 \
    setuptools colorama==0.3.9 PyYAML==3.13 \
    && apk --purge -v del py-pip \
    && rm -rf /var/cache/apk/* \
    && npm install --global yarn


COPY --from=pulumi /pulumi/bin/pulumi /pulumi/bin/pulumi
COPY --from=pulumi /pulumi/bin/*-nodejs* /pulumi/bin/
COPY --from=pulumi /pulumi/bin/pulumi-analyzer-policy /pulumi/bin/

ENV PATH="/pulumi/bin:/root/.local/bin:${PATH}"