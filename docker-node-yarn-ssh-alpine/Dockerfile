FROM docker:18.09.7

RUN apk add --update \
    git \
    zip \
    curl \
    openssh \
    openssl-dev \
    libffi-dev \
    python \
    python-dev \
    python3-dev \
    py-pip \
    build-base \
    docker-compose \
    nodejs=10.24.1-r0 \
    npm=10.24.1-r0 \
    && pip install --upgrade --user \
    cryptography==2.4.2 \
    setuptools colorama==0.3.9 PyYAML==3.13 \
    && apk --purge -v del py-pip \
    && rm -rf /var/cache/apk/* \
    && npm install --global yarn


ENV PATH="/root/.local/bin:${PATH}"