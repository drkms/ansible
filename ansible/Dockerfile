##
FROM debian:latest
MAINTAINER drkms


RUN apt-get update && \
    apt-get install -y ansible && \
    apt-get install -y nano && \
    apt-get install -y openssh-client

RUN mkdir /root/.ssh

##
COPY id_rsa /root/.ssh/