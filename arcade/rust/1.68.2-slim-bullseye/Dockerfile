FROM rust:1.68.2-slim-bullseye
RUN rustup component add rustfmt

RUN apt update -y &&\
    apt upgrade -y
RUN apt install protobuf-compiler pkg-config libssl-dev -y

CMD ["cargo"]