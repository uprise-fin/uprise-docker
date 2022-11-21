FROM heybit/arcade-python:3.11.0-slim-bullseye
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash - && sudo apt-get install -y nodejs npm

RUN npm install -g serverless
RUN npm install -g pnpm