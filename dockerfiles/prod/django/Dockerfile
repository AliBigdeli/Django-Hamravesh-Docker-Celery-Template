# pull official base image
FROM python:3.9-alpine

# maintainers info
LABEL maintainer="bigdeli.ali3@gmail.com"

# installing dependencies
RUN apk add --update --virtual .build-deps \
    build-base \
    postgresql-dev \
    python3-dev \
    libpq


# install dependencies
COPY ./requirements.txt .
RUN pip install --upgrade pip && pip install -r requirements.txt


# set work directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# copy project
COPY ./core .

# collecting static files
CMD python3 manage.py collectstatic --no-input
