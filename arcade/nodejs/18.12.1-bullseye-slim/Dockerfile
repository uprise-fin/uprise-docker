FROM node:18.12.1-bullseye-slim

RUN apt update
RUN apt install -y libssl-dev ca-certificates
RUN update-ca-certificates

CMD ["node"]