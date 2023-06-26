FROM rust:1.70.0-slim-bullseye
RUN rustup component add rustfmt

RUN apt update -y \
    && apt upgrade -y \
    && apt install protobuf-compiler pkg-config libssl-dev -y
    && rm -rf /var/lib/apt/lists/*

CMD ["cargo"]