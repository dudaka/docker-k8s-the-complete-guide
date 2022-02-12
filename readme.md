# Docker and Kubernetes: The Complete Guide

Link: https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/

## Commands

### Manipulating Containers 

* docker run <image name>

* docker create <image name>

* docker start <container id>

* docker ps --all
list all containers including the ones already stopped.

* docker system prune
remove all resources created when working with containers

* docker logs <container id>

* docker stop <container id>
sends a SIGTERM signal to the process inside the container -> take times

* docker kill <container id>
sends a SIGKILL signal -> immediately

* docker exec -it <container id> <command>

* docker run -it <image name> sh

### Building Custom Images

#### Creating a Dockerfile

1. Specify a base image
FROM alpine

2. Run some commands to install additional programs
RUN apk add --update redis

3. Specify a command to run on container startup
CMD ["redis-server"]

* docker build .

* docker build -t <your docker id>/<image name>:<tag (version)> <dir-containing-dockerfile>

#### Generating Docker Image with Docker Commit

1. Start a container
2. Access to the running container 
3. Install dependencies
4. Commit the changes
* docker commit -c 'CMD ["redis-server"]' <running-container-id>
* docker commit -c <starting-command> <running-container-id>

## Simpleweb project

WORKDIR /usr/app

cd simpleweb
docker build -t dudaka/simpleweb .
docker run -p 5000:8080 dudaka/simpleweb