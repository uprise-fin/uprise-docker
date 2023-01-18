FROM rust:1.66.1-slim-bullseye
RUN rustup component add rustfmt

RUN apt update -y &&\
    apt upgrade -y
RUN apt install protobuf-compiler cmake pkg-config libssl-dev -y

CMD ["cargo"]
