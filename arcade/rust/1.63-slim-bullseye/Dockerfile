FROM rust:1.63-slim-bullseye
RUN rustup component add rustfmt

RUN apt update -y &&\
    apt upgrade -y
RUN apt install protobuf-compiler cmake pkg-config libssl-dev -y

CMD ["cargo"]
