FROM node:20.18.3-alpine

RUN apk update \
    && apk upgrade --no-cache \
    && apk add --no-cache curl bash jq yq moreutils make openssl

ENV NO_UPDATE_NOTIFIER=true
RUN npm install -g pnpm@9.15.5 @sentry/cli

# 취약점 처리
RUN mkdir /.cache /.config /.local && \
    chmod 777 /.cache /.config /.local

# 계정 삭제
RUN for user in sync shutdown halt lp uucp games ftp guest squid; do \
    if id "$user" >/dev/null 2>&1; then \
        deluser $user; \
    fi \
done

# profile에 TMOUT 추가
RUN echo -e 'TMOUT=600\nreadonly TMOUT\nexport TMOUT'  >> /etc/profile

# shadow 파일 퍼미션 수정
RUN chmod 400 /etc/shadow

# 공급망 메타데이터
LABEL org.opencontainers.image.source="https://github.com/uprise-fin"
LABEL org.opencontainers.image.licenses="MIT"
LABEL org.opencontainers.image.version="20.18.3-alpine"

# 비루트 사용자(node)로 실행
WORKDIR /app
RUN chown -R node:node /app /.cache /.config /.local
USER node

CMD ["node"]
