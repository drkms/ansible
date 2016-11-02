FROM debian:latest

## SSH Installation
RUN apt-get update && \
    apt-get install -y openssh-server && \
    apt-get install -y nano && \
    apt-get install -y locate && \
    apt-get install -y sudo && \
    apt-get install -y python
    
RUN mkdir /var/run/sshd

## SSH Connection
RUN mkdir /root/.ssh
COPY authorized_keys /root/.ssh/

## Launch the services
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
