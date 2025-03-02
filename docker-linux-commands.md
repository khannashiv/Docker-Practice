######## Some basic linux and dcoker related commands . #######

hostnamectl
uname -a
sudo apt-get update
sudo apt-get install docker.io -y
systemctl status docker
cat /etc/group | grep docker
cat /etc/passwd | grep ubuntu
sudo usermod -aG docker ubuntu
systemctl restart docker
systemctl status docker
docker login
docker images
docker ps or docker ps -a
docker build -t khannashiv/my-django-app .
docker run -d 887a44fb3947 /bin/bash
docker run -it 887a44fb3947 /bin/bash
docker run -dit -p 8000:8000 3e37e9bc3862
docker push khannashiv/docker-image-without-multi-stage:latest


######### Docker Volumes & Bind Mount  || Networking . #############

Commands on docker volumes and networking.

 -- docker volume ls
 -- docker volume create <vol-name>
 -- docker volume inspect <vol-name>
 -- docker volume rm <vol-name>
 -- In order to delete the docker volume >> Make sure it should not be attached with container >> If volume is attached to the container in that case you have to stop the container >> Later you will able to delete the volume .
 -- docker network ls
 -- docker network create <network-name>
 -- docker network inspect <network-name>
 -- docker network rm <network-name>
 -- docker inspect <container-name-or-id>

 To install ping utility inside docker container .

 -- sudo apt-get update
 -- sudo apt-get install -y iputils-ping
 -- docker inspect <container-name / id> | grep IP
 -- docker network create <network-name> ( To create custom bridge network.)
 -- docker network inspect <network-name>
 -- docker network inspect <network-name> | grep IP
 -- docker run -dit --name finance --network=secure-network ubuntu  ( Here finance is name of the docker container, name of the network issecure-network, ubuntu is name of the docker image)
 -- docker run -dit --name=host-demo --network=host ubuntu (Same example as above.)
 -- docker rm -f $(docker ps -aq)
       This command will:
          a) List all containers (both running and stopped) using docker ps -aq.
          b) Pass all those container IDs to docker rm -f, which will forcefully remove each one.

