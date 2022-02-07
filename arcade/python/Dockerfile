FROM python:3.8.12-bullseye

ENV POETRY_VIRTUALENVS_CREATE=False

RUN apt-get update
RUN apt-get install -y \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common \
    apt-utils

RUN python -m pip install --upgrade pip &&\
    pip install poetry
RUN poetry config virtualenvs.create false

CMD ["python"]