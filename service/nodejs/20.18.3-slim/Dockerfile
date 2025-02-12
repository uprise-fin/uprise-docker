FROM node:20.18.3-slim

RUN apt-get update && apt-get upgrade -y && apt-get install -y --no-install-recommends make
RUN apt-get update && apt-get install -y --install-recommends \
    curl \
    jq \
    moreutils \
    chromium \
    ca-certificates \
    openssl \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

ENV NO_UPDATE_NOTIFIER=true
RUN npm install -g pnpm@9.15.5 @sentry/cli

# 취약점 처리
RUN mkdir /.cache /.config /.local && \
    chmod 777 /.cache /.config /.local

# 계정 삭제
RUN awk -F: '$1 !~ /^(root|node)$/ {print $1}' /etc/passwd | xargs -r -n 1 sh -c 'userdel $1' _

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
RUN chown -R node:node /app
USER node

CMD ["node"]
