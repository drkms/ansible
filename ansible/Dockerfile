##
FROM debian:latest
MAINTAINER drkms

## Install of Ansible, and utilities
RUN apt-get update && \
    apt-get install -y gcc && \
    apt-get install -y python-dev libxml2-dev libxslt-dev && \
    apt-get install -y libssl-dev && \
    apt-get install -y nano && \
    apt-get install -y git && \
    apt-get install -y python-setuptools && \
    apt-get install -y openssh-client

## Prepare SSh Authentication
RUN mkdir /root/.ssh
COPY id_rsa /root/.ssh/

## A few conf keys
RUN echo 'alias l="ls -la"' >> ~/.bashrc

## Prepare ANSIBLE installation
RUN easy_install pip
RUN pip install paramiko PyYAML Jinja2 httplib2 six

## Ugly hack to enable bash during docker build
RUN rm /bin/sh && ln -s /bin/bash /bin/sh

## Install from source
RUN git clone git://github.com/ansible/ansible.git --recursive
RUN cd ./ansible
RUN source /ansible/hacking/env-setup

## Pre-Configure Ansible
RUN mkdir /etc/ansible
RUN touch /etc/ansible/hosts
RUN echo -e "\n[webserver]\nblank" >> /etc/ansible/hosts
RUN cp /ansible/examples/ansible.cfg /etc/ansible/
RUN sed -i 's/#host_key_checking = False/host_key_checking = False/g' /etc/ansible/ansible.cfg

## Editing PATH
RUN echo "export PYTHONPATH=/ansible/lib" >> ~/.bashrc
RUN echo "export PATH=/ansible/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"  >> ~/.bashrc
RUN echo "export MANPATH=/ansible/docs/man:"  >> ~/.bashrc

## CMD
