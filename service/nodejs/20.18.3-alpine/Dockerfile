FROM node:20.18.3-alpine

RUN apk update \
    && apk add --no-cache curl bash jq yq moreutils make

ENV NO_UPDATE_NOTIFIER=true
RUN npm install -g pnpm@9.15.5 @sentry/cli

# 취약점 처리
RUN mkdir /.cache \
    && chmod 777 /.cache \
    && mkdir /.config \
    && chmod 777 /.config \
    && mkdir /.local \
    && chmod 777 /.local
# 계정 삭제
RUN echo "sync shutdown halt lp uucp games ftp guest squid" | tr ' ' '\n' | xargs -I {} deluser {}
# profile에 TMOUT 추가
RUN echo -e 'TMOUT=600\nreadonly TMOUT\nexport TMOUT'  >> /etc/profile
# shadow 파일 퍼미션 수정
RUN chmod 400 /etc/shadow

CMD ["node"]
