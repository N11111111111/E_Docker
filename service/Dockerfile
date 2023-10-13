FROM python:3.9-alpine3.16

# set work directory
WORKDIR /usr/src/service/


# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install psycopg2 dependencies
RUN apk update \
    && apk add postgresql-client build-base postgresql-dev gcc python3-dev musl-dev
# install dependencies
RUN pip install --upgrade pip

COPY ./requirements.txt .

RUN pip install -r ./requirements.txt

COPY ./entrypoint.sh .


# copy project
#RUN adduser --disabled-password service-user
#USER service-user

RUN mkdir /usr/src/service/static
RUN mkdir /usr/src/service/media

COPY . .


ENTRYPOINT ["/usr/src/service/entrypoint.sh"]

















