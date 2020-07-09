FROM rust:1.44.1-buster
RUN curl -sL https://sentry.io/get-cli/ | bash

# docker repo
RUN apt-get update && apt-get install --no-install-recommends -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository \
    "deb [arch=amd64] https://download.docker.com/linux/debian \
    $(lsb_release -cs) \
    stable"

# docker
RUN apt-get update && apt-get install --no-install-recommends -y docker-ce docker-ce-cli containerd.io

# docker-compose
RUN curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" \
    -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose

# yaml
RUN apt install -y python3-pip && pip3 install pyyaml