# specify the node base image with your desired version node:<version>
FROM node:8

RUN apt-get update && apt-get install nano

WORKDIR /home/nodejs/app

# copy all application files
COPY . .
COPY ./docker/config ./src/config

RUN yarn install
