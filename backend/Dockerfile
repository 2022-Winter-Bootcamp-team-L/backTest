# pull official base image
FROM python:3.9.16-alpine3.16

ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

ARG DJANGO_ALLOWED_HOSTS
ARG DJANGO_SECRET_KEY
ARG DJANGO_CORS_ORIGIN_WHITELIST

ENV DJANGO_ALLOWED_HOSTS $DJANGO_ALLOWED_HOSTS
ENV DJANGO_SECRET_KEY $DJANGO_SECRET_KEY
ENV DJANGO_CORS_ORIGIN_WHITELIST $DJANGO_CORS_ORIGIN_WHITELIST

WORKDIR /backend
COPY requirements.txt /backend/

RUN pip install --upgrade pip
RUN pip install -r requirements.txt
RUN pip install Pillow
RUN apk update && apk add --no-cache --virtual bash gcc musl-dev linux-headers jpeg-dev zlib-dev mariadb-dev libffi-dev
#RUN apk update

#RUN apk add mysql mysql-client
#여기까지 에러 없음
RUN pip install mysqlclient

COPY . /backend/