FROM docker:18.09.7

RUN apk add --update \
    git \
    zip \
    python \
    python-dev \
    py-pip \
    build-base \
    nodejs=10.19.0-r0 \
    npm=10.19.0-r0 \
    && pip install --upgrade --user \
    awscli==1.16.193 \
    awsebcli==3.15.2 \
    setuptools colorama==0.3.9 PyYAML==3.13 \
    && apk --purge -v del py-pip \
    && rm -rf /var/cache/apk/*

ENV PATH="/root/.local/bin:${PATH}"

RUN aws configure set preview.cloudfront true
