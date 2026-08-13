Objective

The objective of Task 3 is to containerize a simple web application using Docker and Docker Compose.

The application should be packaged into a Docker image, executed as a container, and configured to restart automatically if the container stops.

Requirements

The task requires:

Create a Dockerfile
Build the Docker image
Run the container
Use Docker Compose
Configure automatic container restart
Application

A simple web application was used for the Dockerization process.

The application files were placed inside the project directory under:

application/

The Dockerfile was created in the project root.

Dockerfile

A Dockerfile was created to define how the application image should be built.

It specifies:

Base image
Application files
Required configuration
Exposed application port
Command required to start the application

Docker uses the Dockerfile instructions to create a reproducible application image.

Docker Image

After creating the Dockerfile, a Docker image was built from it.

The image contains the application and everything required to run it inside a container.

The image was verified after the build to ensure that it was successfully created.

Docker Container

The Docker image was used to create a running container.

The container provides an isolated environment in which the application can run independently of the host environment.

The running container was checked to verify that the application was successfully started.

Docker Compose

A docker-compose.yml file was created to define the application container.

Docker Compose makes it easier to configure and run the application using a single configuration file.

The Compose configuration contains the required application service and its port mapping.

Automatic Restart

Automatic restart was configured for the container.

This allows Docker to restart the application automatically if the container stops unexpectedly.

This is useful for improving application availability.

## Commands Used
# Check Docker
docker --version

# Check Docker Compose
docker compose version

# Build Docker image
docker build -t devops-app:v1 .

# Check Docker images
docker images

# Run container
docker run -d --name devops-app -p 8080:80 --restart unless-stopped devops-app:v1

# Check running containers
docker ps

# Check all containers
docker ps -a

# Build and start using Docker Compose
docker compose up -d --build

# Check Compose containers
docker compose ps

# View container logs
docker logs devops-app

# Stop Compose application
docker compose down