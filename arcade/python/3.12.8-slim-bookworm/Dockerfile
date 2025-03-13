FROM python:3.12.9-slim-bookworm

RUN apt update  \
    && apt install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common \
    apt-utils \
    g++ \
    make \
    cmake \
    unzip \
    libcurl4-openssl-dev \
    pkg-config \
    libmariadb-dev \
    git \
    jq \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir --upgrade pip awscli && pip install --no-cache-dir poetry && poetry config virtualenvs.create false
RUN curl -sL https://sentry.io/get-cli/ | bash