FROM python:3.10.12-slim-bullseye

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
    libmariadb-dev \
    git \
    jq \
    && rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir --upgrade pip awscli && pip install --no-cache-dir poetry && poetry config virtualenvs.create false
RUN curl -sL https://sentry.io/get-cli/ | bash

# 취약점 처리
RUN mkdir /.cache \
    && chmod 777 /.cache \
    && mkdir /.config \
    && chmod 777 /.config \
    && mkdir /.local \
    && chmod 777 /.local \
    && chmod 400 /etc/shadow

# profile에 TMOUT 추가
RUN echo -e 'TMOUT=600\nreadonly TMOUT\nexport TMOUT'  >> /etc/profile