# Docker Container
[main](../../README.md) | [devops](../README.md) | [docker](README.md) | [container](Container.md)

## About Container
Container is a component that automates the implementation of an application.

A container is made up of one or more images.

---

## Docker Container Commands
```sh
# Run a container
docker container run <container_image_name>

# Run a container in background
docker container run -d <image_image_name>

# Run and name a container
docker container run --name <my_custom_container_name> <container_image_name>

# Run a container and then remove it when finish
docker container run --rm <container_image_name>

# Run a container and define an external port associated with a internal port
docker container run -d -p 8080:80 <container_image_name>

# Run a container and open the interaction console
docker container run -it <container_image_name> /bin/bash

# Execute the interaction console of a running container
docker exec -it <container_id_or_name>

# Start a stopped container
docker container start <container_id_or_name>

# Stop a running container
docker container stop <container_id_or_name>

# List running containers
docker container ls

# List all containers (running and stopped)
docker contaier ls -a

# List all containers ID
docker container ls -a -q

# List running images
docker image ls

# Remove a stopped container
docker container rm <container_id_or_name>

# Remove a running container using a force param
docker container rm -f <container_id_or_name>

# Remove all containers with conditional command
docker container rm -f $(docker container ls -aq)

# Build a Dockerfile (current folder)
docker build -t <image_name> .

# Build a Dockerfile (other folder)
docker build -t <custom_image_name> ../../<folder_name>

# Build a Dockerfile without cache
docker build -t <image_name> . --no-cache

# Remove all unused images
docker iamge prune

# Rename image
docker tag <current_image_name> <new_image_name>
```

<br>

## Docker Container Samples

```sh
# Set and run a postgres container
docker container run -d -p 5432:5432 -e POSTGRES_DB=aula -e POSTGRES_USER=devops -e POSTGRES_PASSWORD=12345678 postgres

# Run an Ubuntu container and open the interaction console
docker container run -it ubuntu /bin/bash
```
