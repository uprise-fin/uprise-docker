FROM node:14-alpine3.15 

RUN apk -U upgrade \
    && apk add --no-cache \
    git
RUN npm install -g pnpm@^7.5.0 lerna 
