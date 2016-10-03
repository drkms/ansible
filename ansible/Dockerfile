##
FROM debian:latest
MAINTAINER drkms

## Install of Ansible, and utilities
RUN apt-get update && \
    apt-get install -y ansible && \
    apt-get install -y nano && \
    apt-get install -y openssh-client

## Prepare SSh Authentication
RUN mkdir /root/.ssh
COPY id_rsa /root/.ssh/

## Pre-Configure Ansible

RUN echo "\n[webserver]\nblank" >> /etc/ansible/hosts
RUN sed -i 's/#host_key_checking = False/host_key_checking = False/g' /etc/ansible/ansible.cfg

## CMD
