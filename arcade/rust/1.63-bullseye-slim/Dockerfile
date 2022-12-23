FROM rust:1.63-bullseye-slim
RUN rustup component add rustfmt

RUN apt update -y &&\
    apt upgrade -y
RUN apt install protobuf-compiler cmake -y

CMD ["cargo"]
