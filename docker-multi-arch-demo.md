Machine 1 & 2 both were created on AWS i.e one is with AMD processor other with Arm processor .

Machine 1 : Commands executed on Ubuntu-Amd processor. 

-- sudo apt install docker-buildx && sudo apt update && sudo apt install docker.io -y
-- sudo docker buildx version
-- sudo docker --version
-- sudo usermod -aG docker ubuntu
-- sudo docker buildx ls
-- sudo docker login
-- cat Dockerfile
  - FROM ubuntu:latest
  - CMD ["echo", "I'm working on multi-arch-demo"]
-- sudo docker buildx build --push -t khannashiv/multiarchdemo:v1 .     # Without multiarch docker image 
-- sudo docker buildx build --platform linux/amd64,linux/arm64,linux/amd64/v3,linux/amd64/v2 --push -t khannashiv/multiarchdemo:v2 .

-- sudo docker buildx create --name multiarch --platform linux/amd64,linux/arm64,linux/arm/v7,linux/arm/v6,linux/amd64/v3 --driver docker-container --bootstrap --use

Machine 2 : Commands executed on Ubuntu-Arm processor. 


-- sudo apt install docker-buildx && sudo apt update && sudo apt install docker.io -y
-- sudo docker buildx version
-- sudo docker --version
-- sudo usermod -aG docker ubuntu
-- sudo docker buildx ls
-- sudo docker login
-- sudo docker pull khannashiv/multiarchdemo:v1
  Error : v1: Pulling from khannashiv/multiarchdemo no matching manifest for linux/arm64/v8 in the manifest list entries

-- sudo docker pull khannashiv/multiarchdemo:v2
  Output displayed as : v2: Pulling from khannashiv/multiarchdemo
              Digest: sha256:579e39b6893ea135849c25d259913dee2b1b713b6daec0f099630dc8c16bea1e
              Status: Image is up to date for khannashiv/multiarchdemo:v2
              docker.io/khannashiv/multiarchdemo:v2

-- sudo docker run khannashiv/multiarchdemo:v2
    Ouput displayed as : I'm working on multi-arch-demo
