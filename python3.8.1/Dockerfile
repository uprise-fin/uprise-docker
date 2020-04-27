FROM python:3.8.1-buster

RUN apt-get update
RUN apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common \
    apt-utils

RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
RUN apt-get update
RUN apt-get install -y docker-ce docker-ce-cli containerd.io
RUN pip install docker-compose

RUN apt-get install -y \
    libzstd-dev \
    liblz4-dev \
    libbz2-dev \
    zlib1g-dev \
    libsnappy-dev \
    libgflags-dev

RUN git clone https://github.com/facebook/rocksdb.git
WORKDIR rocksdb
RUN git checkout v6.6.4
RUN make shared_lib
RUN make install-shared INSTALL_PATH=/usr
WORKDIR /
RUN rm -rf rocksdb

RUN pip install poetry
RUN mkdir /.cache
RUN chmod 777 /.cache
RUN mkdir /.config
RUN chmod 777 /.config
RUN mkdir /.local
RUN chmod 777 /.local

RUN curl -sL https://sentry.io/get-cli/ | bash
