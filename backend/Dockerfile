FROM python:3.8.1-alpine
MAINTAINER Anton

ENV PYTHONUNBUFFERED 1

COPY ./requirements.txt /requirements.txt
RUN apk add --update --no-cache postgresql-client jpeg-dev
RUN apk add --update --no-cache --virtual .tmp-build-deps \
      gcc libc-dev linux-headers postgresql-dev musl-dev zlib zlib-dev
RUN pip install -r /requirements.txt
RUN apk del .tmp-build-deps

RUN mkdir /api
WORKDIR /backend/api
COPY ./api /

RUN adduser -D user
RUN chown -R user:user /api/
RUN chmod -R 755 /api/
USER user