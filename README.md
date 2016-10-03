# Ansible

The current project is not astonishing. I'm new in Docker, and I wanted to share this files.

## Requirement
You must have Docker Engine installed, and you must have launched the Daemon.

For more information on how to install Docker, please refer to the [official documentation](https://docs.docker.com/engine/installation/)

You must also have [docker-compose](https://docs.docker.com/compose/install/)

## Installation

First clone the project.
```
git clone https://github.com/drkms/ansible.git
```
Then, you should enter the project, and set up a new SSH key.

Build each image, and run everything :
```
cd ansible
cp your_ssh_key-rsa ansible/id_rsa
cp your_ssh_key-rsa.pub blank/authorized_keys
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