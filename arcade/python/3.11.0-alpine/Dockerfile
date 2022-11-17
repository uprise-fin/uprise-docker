FROM python:3.11.0-alpine

RUN apk update
# use --virtual for easily remove libs after build everything
# remove build only libs by "RUN apk del build-deps"
RUN apk add --no-cache --virtual build-deps build-base mariadb-connector-c-dev curl

RUN apk add git ca-certificates

RUN pip install --upgrade pip
RUN pip install poetry
RUN poetry config virtualenvs.create false

# 취약점 처리
RUN mkdir /.cache
RUN chmod 777 /.cache
RUN mkdir /.config
RUN chmod 777 /.config
RUN mkdir /.local
RUN chmod 777 /.local

RUN curl -sL https://sentry.io/get-cli/ | sh

RUN echo "sync shutdown halt lp uucp games ftp guest squid" | tr ' ' '\n' | xargs -I {} deluser {}
# profile에 TMOUT 추가
RUN echo -e 'TMOUT=600\nreadonly TMOUT\nexport TMOUT'  >> /etc/profile
# shadow 파일 퍼미션 수정
RUN chmod 400 /etc/shadow