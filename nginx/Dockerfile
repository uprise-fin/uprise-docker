FROM nginx:1.23.2-alpine
RUN apk update && apk add nginx-mod-http-headers-more
COPY nginx.conf /etc/nginx/
