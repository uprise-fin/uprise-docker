FROM node:20.12.1-bullseye-slim

RUN apt-get update \
    && apt-get install -y curl bash libssl1.1 \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sL https://sentry.io/get-cli/ | sh

# 계정 삭제
RUN awk -F: '$1 !~ /^(root|node)$/ {print $1}' /etc/passwd | xargs -r -n 1 sh -c 'userdel $1' _

# profile에 TMOUT 추가
RUN echo -e 'TMOUT=600\nreadonly TMOUT\nexport TMOUT'  >> /etc/profile

# 취약점 처리
RUN mkdir /.cache \
    && chmod 777 /.cache \
    && mkdir /.config \
    && chmod 777 /.config \
    && mkdir /.local \
    && chmod 777 /.local \
    && chmod 400 /etc/shadow

CMD ["node"]
