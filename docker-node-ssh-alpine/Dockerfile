FROM docker:18.09.7

RUN apk add --update \
    git \
    zip \
    openssh \
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
    && pip install --upgrade --user \
    cryptography==2.4.2 \
    setuptools colorama==0.3.9 PyYAML==3.13 \
    && apk --purge -v del py-pip \
    && rm -rf /var/cache/apk/*

ENV PATH="/root/.local/bin:${PATH}"