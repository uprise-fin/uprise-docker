FROM debian:buster-slim
RUN apt update
RUN apt install -y git wget
RUN wget https://github.com/cli/cli/releases/download/v0.7.0/gh_0.7.0_linux_amd64.deb
RUN apt install -y ./gh_*_linux_amd64.deb
RUN apt install hub
