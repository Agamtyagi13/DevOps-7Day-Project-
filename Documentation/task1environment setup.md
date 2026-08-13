Task 1 – Environment Setup
Objective

The objective of this task is to prepare a DevOps environment by installing the required DevOps tools and verifying that they are working correctly.

The environment was prepared using Ubuntu on WSL2.

Tools Installed

The following tools were installed and verified:

Git
Docker
Docker Compose
Jenkins
Kind (Kubernetes)
kubectl
1. Git Installation

Git was installed to provide version control and manage the project's source code.

After installation, the Git version was checked to confirm successful installation.

Verification: Git was successfully installed and available from the terminal.

2. Docker Installation

Docker was installed to provide containerization capabilities for the project.

Docker was verified by checking its version and confirming that the Docker daemon was working correctly.

Verification: Docker was successfully installed and operational.

3. Docker Compose Installation

Docker Compose was configured for managing multi-container applications.

Its version was checked after installation to verify that it was available and working.

Verification: Docker Compose was successfully installed.

4. Jenkins Installation

Jenkins was installed as the CI/CD automation server.

Java was configured as a prerequisite for Jenkins, and the Jenkins service was started and verified.

Verification: Jenkins was successfully installed and the Jenkins service was running.

5. Kubernetes Installation

Kind was used to create a local Kubernetes environment.

A Kubernetes cluster was created using Kind for local development and testing.

Verification: The Kubernetes node was checked using kubectl and confirmed to be in a Ready state.

6. kubectl Installation

kubectl was installed as the command-line tool for communicating with the Kubernetes cluster.

The client version was checked after installation.

Verification: kubectl was successfully installed and able to communicate with the Kind cluster.

### COMMAND USED


# System update
sudo apt update
sudo apt upgrade -y

# Git
git --version

# Docker
docker --version
docker info

# Docker Compose
docker compose version

# Java / Jenkins
java -version
sudo systemctl status jenkins
jenkins --version

# Kind
kind version

# Create Kubernetes cluster
kind create cluster --name devops-cluster

# kubectl
kubectl version --client

# Verify Kubernetes
kubectl get nodes
kubectl cluster-info