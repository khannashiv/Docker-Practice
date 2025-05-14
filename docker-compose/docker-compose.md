# Docker Compose

Docker Compose is a valuable tool for managing multi-container applications. It simplifies the process of defining, running, and managing containerized applications.

## Docker Compose Uses

### Local Development

- **Benefit**: Rapid local development.
- **Use Case**: DevOps engineers write Docker Compose YAML files and share them with developers. Developers can then easily run the application without memorizing complex commands. Just `docker-compose up`.

### Continuous Integration and Continuous Deployment (CI/CD)

- **Benefit**: Streamlined CI/CD pipelines.
- **Use Case**: For each pull request, you can set up a virtual machine (VM) and install Docker. Your CI/CD pipeline can then run commands like `docker-compose up` and `docker-compose down` to validate changes.

### Testing

- **Benefit**: Efficient and consistent testing environments.
- **Use Case**: Create isolated testing environments where the application's various services can be tested together, ensuring compatibility and performance across all integrated services.

## Docker Swarm vs. Kubernetes

- **Docker Swarm**: Docker's native clustering and orchestration tool, designed for simpler, smaller-scale deployments.
- **Kubernetes**: A more comprehensive orchestration system, ideal for complex, large-scale container deployments.

While Docker Swarm is a good entry point for simpler clustering, Kubernetes offers a broader set of features and is often considered more robust for larger production environments.

## Basic Docker Compose Commands

- `docker-compose up`: Start all the services defined in your `docker-compose.yml` file.
- `docker-compose up -d`: Run the containers in the background.
- `docker-compose down`: Stop and remove all the containers, networks, and volumes defined in your `docker-compose.yml`.
- `docker-compose logs`: Show the logs from the running containers.
- `docker-compose logs -f`: Follow the logs in real-time.
- `docker-compose build`: Build the images defined in the `docker-compose.yml` file. If you make changes to the Dockerfiles, run this command to rebuild the images.
- `docker-compose up --scale <service_name>=<number_of_instances>`
- `docker-compose ps`: Show the status of all the containers managed by Docker Compose.
- `docker-compose stop`: Stop the services but don't remove the containers.
- `docker-compose --version`: View the current version of Docker Compose.
- `docker-compose stop <service_name>`: Stop a specific service without affecting others.

## Reference Documentation

- [Docker Compose Documentation](https://docs.docker.com/compose/)
- [Awesome Compose](https://github.com/docker/awesome-compose) - For practice with Docker Compose.

## Implemented Project: Robot-Shop

- [Robot-Shop GitHub Repository](https://github.com/khannashiv/robot-shop)
- **AWS EC2 Instance**: Ubuntu + t2.medium + 15 GB Disk / EBS volume.
- **Setup Commands**:
  - `sudo apt-get update && apt-get install docker-compose`
  - `git clone <repo-url>`
  - Navigate to the directory where the Docker Compose YAML file is located.
  - To run the project locally:
    - `docker-compose pull`
    - `docker-compose up` or `docker-compose up -d`
    - `docker-compose down`
  - Verify with `docker ps` and `docker images`.
  - Access the application at `http://localhost:8080` or `http://<Public-IP-of-EC2>:8080/`.
