# Docker and Linux Commands

## Table of Contents
- [Basic Linux Commands](#basic-linux-commands)
- [Docker Installation and Setup](#docker-installation-and-setup)
- [Docker Commands](#docker-commands)
- [Docker Volumes](#docker-volumes)
- [Docker Networking](#docker-networking)
- [Miscellaneous](#miscellaneous)

## Basic Linux Commands
```bash
hostnamectl        # Show system hostname
uname -a           # Show system information


#### Docker Installation and Setup

sudo apt-get update                              # Update package list
sudo apt-get install docker.io -y                # Install Docker
systemctl status docker                          # Check Docker service status
cat /etc/group | grep docker                     # Check Docker group
cat /etc/passwd | grep ubuntu                    # Check user 'ubuntu'
sudo usermod -aG docker ubuntu                   # Add 'ubuntu' user to Docker group
systemctl restart docker                         # Restart Docker service
systemctl status docker                          # Check Docker service status again

#### Docker Commands 

docker login                                     # Log in to Docker
docker images                                    # List Docker images
docker ps                                        # List running containers
docker ps -a                                     # List all containers
docker build -t khannashiv/my-django-app .       # Build Docker image
docker run -it <image-name | image-id> /bin/bash # Run container interactively
docker run -dit -p 8000:8000 <image-name | image-id> # Run container with port mapping
docker run -e MY_ENV_VAR=value -d <image-name>   # Run container with environment variable
docker push khannashiv/docker-image-without-multi-stage:latest # Push image to repository

##### Docker Volumes .

docker volume ls                                 # List Docker volumes
docker volume create <vol-name>                  # Create Docker volume
docker volume inspect <vol-name>                 # Inspect Docker volume
docker volume rm <vol-name>                      # Remove Docker volume
docker run -v /host/path:/container/path -d <image-name> # Run container with volume


#### Docker Networking .

docker network ls                                # List Docker networks
docker network create <network-name>             # Create Docker network
docker network inspect <network-name>            # Inspect Docker network
docker network rm <network-name>                 # Remove Docker network
docker inspect <container-name-or-id>            # Inspect container

### To install the ping utility inside a Docker container:

sudo apt-get update                              # Update package list
sudo apt-get install -y iputils-ping             # Install ping utility
docker inspect <container-name / id> | grep IP   # Get container IP
docker network create <network-name>             # Create custom bridge network
docker network inspect <network-name>            # Inspect network
docker network inspect <network-name> | grep IP  # Get network IP
docker run -dit --name finance --network=secure-network ubuntu # Run container with custom network
docker run -dit --name=host-demo --network=host ubuntu # Run container with host network
docker rm -f $(docker ps -aq)                    # Remove all containers

        # This command i.e. on line # 67 will:
        #         List all containers (both running and stopped) using docker ps -aq.
        #         Pass all those container IDs to docker rm -f, which will forcefully remove each one

# Miscellaneous

docker run -e MY_ENV_VAR=value -d <image-name>   # Run container with environment variable