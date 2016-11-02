# Ansible

Ansible is a really nice Configuration Tool. It can help you in many different way. But when I got to work on playbooks, or when I just want to test something, I usually dont want to launch my playbook 'for real'. The purpose of this project is to provide a Docker Environment to write and work around playbook in a SandBox.

## Requirement

You must have Docker Engine installed and running.

For more information on how to install Docker, please refer to the [official documentation](https://docs.docker.com/engine/installation/)

You must also have [docker-compose](https://docs.docker.com/compose/install/)

For more information about Ansible, plese refer to the [official documentation](http://docs.ansible.com/ansible/index.html)

## Features

- Debian Container with Ansible 2.3.0
- Debian Container with a blank environment and a running OpenSSH server on it

## Installation

First clone the project.
```
git clone https://github.com/drkms/ansible.git
```
You should set up a bundle of private/public SSH keys.

You can do it manully, or do it by running the "build" script
```
./build
```

You can now build the images using Docker :

```
cd ansible 
docker build -t ansible .
```
... and ...
```
cd ../blank
docker build -t blank .
```

Now you got your Docker images "ansible" and "blank", you should build the environment :
```
docker-compose up -d
```

You can now open a bash on the "ansible" image, in order to try to play with Ansible on your "blank" image ...
```
docker-compose run ansible bash
```
Now, test the whole environment with a simple Ansible cmd, per exemple :
```
ansible all -m ping
```

Place your playbook to be tested into the 'playbook' folder, you will find them into the 'ansible' image, in ~/playbook/