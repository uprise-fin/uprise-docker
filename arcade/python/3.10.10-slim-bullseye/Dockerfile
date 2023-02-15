FROM python:3.10.10-slim-bullseye

RUN apt update
RUN apt install -y \
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
    git

RUN curl -fsSL https://get.docker.com -o get-docker.sh
RUN bash get-docker.sh

RUN pip install --upgrade pip
RUN pip install --upgrade awscli
RUN pip install poetry
RUN poetry config virtualenvs.create false

# 취약점 처리
RUN mkdir /.cache
RUN chmod 777 /.cache
RUN mkdir /.config
RUN chmod 777 /.config
RUN mkdir /.local
RUN chmod 777 /.local

RUN curl -sL https://sentry.io/get-cli/ | bash

# profile에 TMOUT 추가
RUN echo -e 'TMOUT=600\nreadonly TMOUT\nexport TMOUT'  >> /etc/profile
# shadow 파일 퍼미션 수정
RUN chmod 400 /etc/shadow