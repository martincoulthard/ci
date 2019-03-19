FROM ubuntu:16.04

RUN apt-get update && apt-get install -y \
    python-pip python-dev build-essential \
    curl \
    zip \
    git

RUN pip install --upgrade pip==9.0.3 && \
    pip install --upgrade virtualenv && \
    pip install awscli awsebcli

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -

RUN apt-get install -y nodejs

RUN npm install -g yarn git+https://git@github.com/backslashbuild/dockerrun-env-injector.git

RUN mkdir /build

RUN VER="17.03.0-ce" && \
    curl -L -o /tmp/docker-$VER.tgz https://get.docker.com/builds/Linux/x86_64/docker-$VER.tgz && \
    tar -xz -C /tmp -f /tmp/docker-$VER.tgz && \
    mv /tmp/docker/* /usr/bin

RUN aws configure set preview.cloudfront true

COPY ./swagger-codegen-cli.jar /build