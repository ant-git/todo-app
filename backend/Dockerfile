FROM python:3.8.1-alpine
MAINTAINER Anton

ENV PYTHONUNBUFFERED 1

COPY ./requirements.txt /requirements.txt
RUN pip install -r /requirements.txt

RUN mkdir /api
WORKDIR /backend/api
COPY ./api /

RUN adduser -D user
RUN chown -R user:user /api/
RUN chmod -R 755 /api/
USER user