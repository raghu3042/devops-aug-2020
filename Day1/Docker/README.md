# Docker Commands

### Install docker in CentOS
sudo yum install -y yum-utils

sudo yum-config-manager
    --add-repo
    https://download.docker.com/linux/centos/docker-ce.repo

sudo yum install docker-ce docker-ce-cli containerd.io

sudo systemctl enable docker && sudo systemctl start docker

### Granting regular(non-admin) user to issue docker commands
sudo usermod -aG docker jegan
sudo su jegan

### Checking the user groups a unix user belongs to
id

### Find docker version
docker --version

### Checking details about docker installation
docker info

### Listing all docker images from Local Docker Registry
docker images

### Listing all currently running containers
docker ps

### Listing all containers irrespective of their running state
docker ps -a

### Listing all running container ids
docker ps -q

### List all container ids
docker ps -aq

### Stopping a running container
docker stop ubuntu1
docker stop ubuntu1 ubuntu2
docker stop $(docker ps -q)

### Deleting containers
docker stop ubuntu1 && docker rm ubuntu1
docker rm -f ubuntu1

### Deleting an image from local docker registry
docker rmi hello-world:latest

### Finding more details about container
docker inspect ubuntu1

### Finding more details about a docker image
docker image inspect ubuntu:16.04

### Creating a docker container in foreground(interactive) mode
docker run -it --name ubuntu1 --hostname ubuntu1 ubuntu:16.04 /bin/bash

### Creating a docker container in daemon(background) mode
docker run -dit --name ubuntu1 --hostname ubuntu1 ubuntu:16.04 /bin/bash

### Opening a second shell inside a running container
docker exec -it ubuntu1 /bin/bash

### Find IP address of a container
docker exec -it ubuntu1 hostname -i
docker inspect ubuntu1 | grep IPA
docker inspect -f "{{ .NetworkSettings.IPAddress }}" ubuntu1

### Finding hostname of a container
docker exec -it ubuntu1 hostname 
