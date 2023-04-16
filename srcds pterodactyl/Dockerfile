# Tag - ptero
FROM alpine:latest
LABEL maintainer='Baldurr'
RUN apk add --no-cache sudo bash curl jq wget tar nodejs npm && adduser --disabled-password --home /home/container container

USER container
ENV  USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
COPY ./package.json /package.json
COPY ./package-lock.json /package-lock.json

USER root
WORKDIR /home/container
RUN npm install pm2 -g --force
RUN npm install

USER container
WORKDIR /home/container

EXPOSE 9591
CMD ["/bin/bash", "/entrypoint.sh"]