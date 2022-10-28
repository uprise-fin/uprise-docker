FROM node:12.18.3-buster-slim

RUN apt update
RUN apt install -y libssl-dev ca-certificates
RUN update-ca-certificates

CMD ["node"]