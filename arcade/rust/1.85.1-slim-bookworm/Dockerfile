FROM rust:1.85.1-slim-bookworm
RUN rustup component add rustfmt

RUN apt update -y \
    && apt upgrade -y \
    && apt install protobuf-compiler pkg-config libssl-dev git  -y \
    && rm -rf /var/lib/apt/lists/*

CMD ["cargo"]