# Multi-Architecture Docker Demo

This guide demonstrates building and running a Docker image for multiple architectures (AMD and ARM) using Docker Buildx.

## Setup

The demo is executed on two AWS instances:
1. **Machine 1**: Ubuntu with AMD processor
2. **Machine 2**: Ubuntu with ARM processor

---

## Machine 1: Steps for AMD Processor

### Install Docker and Buildx
```bash
sudo apt update
sudo apt install docker-buildx docker.io -y
sudo docker buildx version
sudo docker --version
sudo usermod -aG docker ubuntu
```

### Verify Buildx Installation
```bash
sudo docker buildx ls
```

### Authenticate Docker CLI
```bash
sudo docker login
```

### Create a Simple `Dockerfile`
```Dockerfile
FROM ubuntu:latest
CMD ["echo", "I'm working on multi-arch-demo"]
```

### Build and Push Docker Images

1. Build a regular image:
   ```bash
   sudo docker buildx build --push -t khannashiv/multiarchdemo:v1 .
   ```

2. Build a multi-architecture image:
   ```bash
   sudo docker buildx build --platform linux/amd64,linux/arm64 --push -t khannashiv/multiarchdemo:v2 .
   ```

3. Create a Buildx builder instance for multi-architecture:
   ```bash
   sudo docker buildx create --name multiarch --platform linux/amd64,linux/arm64 --driver docker-container --bootstrap --use
   ```

---

## Machine 2: Steps for ARM Processor

### Install Docker and Buildx
```bash
sudo apt update
sudo apt install docker-buildx docker.io -y
sudo docker buildx version
sudo docker --version
sudo usermod -aG docker ubuntu
```

### Verify Buildx Installation
```bash
sudo docker buildx ls
```

### Authenticate Docker CLI
```bash
sudo docker login
```

### Pull Docker Images

1. Attempt to pull `v1` (Expected Error for ARM):
   ```bash
   sudo docker pull khannashiv/multiarchdemo:v1
   ```

   **Error**:
   ```
   v1: Pulling from khannashiv/multiarchdemo
   no matching manifest for linux/arm64/v8 in the manifest list entries
   ```

2. Pull the multi-architecture image `v2`:
   ```bash
   sudo docker pull khannashiv/multiarchdemo:v2
   ```

   **Output**:
   ```
   v2: Pulling from khannashiv/multiarchdemo
   Digest: sha256:579e39b6893ea135849c25d259913dee2b1b713b6daec0f099630dc8c16bea1e
   Status: Image is up to date for khannashiv/multiarchdemo:v2
   docker.io/khannashiv/multiarchdemo:v2
   ```

### Run the Docker Image
```bash
sudo docker run khannashiv/multiarchdemo:v2
```

**Output**:
```
I'm working on multi-arch-demo
```

---

## Notes and Troubleshooting

- **Error for `v1` Image**: The `v1` image does not support ARM (linux/arm64 architecture). Build multi-architecture images using Buildx with the `--platform` flag.
- **Buildx Compatibility**: Ensure Docker Buildx is properly installed and supported on your system.

---

This guide shows how to build Docker images for multiple architectures and run them on different processors (AMD and ARM). Happy Dockering!
