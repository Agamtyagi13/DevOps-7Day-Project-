1. Project Overview
# DevOps 7-Day Project

This project demonstrates a basic DevOps workflow for deploying and managing a containerized web application.

The project covers:

- Git and GitHub
- Docker
- Docker Compose
- Jenkins CI
- Kubernetes
- Prometheus
- Grafana
- Bash automation

The workflow starts from application source code and progresses through containerization, CI, Kubernetes deployment, monitoring, and automation.

2. Folder Structure
DevOps-7Day-Project/
├── application/
│   └── index.html
├── Docker/
│   ├── Dockerfile
│   └── docker-compose.yml
├── Documentation/
├── kubernetes/
│   ├── deployment.yaml
│   └── service.yaml
├── monitoring/
├── scripts/
│   └── deploy.sh
├── screenshots/
├── Jenkinsfile
├── README.md
└── ...

3. Installation Steps
## Installation Steps

The project was developed and tested using WSL Ubuntu.

### Prerequisites

- Ubuntu / WSL
- Git
- Docker
- Docker Compose
- Jenkins
- kubectl
- Kind
- Helm
- Prometheus
- Grafana

### Clone Repository

```bash
git clone https://github.com/Agamtyagi13/DevOps-7Day-Project-.git
cd DevOps-7Day-Project

## Verify Tools
git --version
docker --version
docker compose version
kubectl version --client
kind version
helm version

---

# 4. Docker Commands

Document the commands you actually used for Task 3.

```markdown
## Docker

### Build Docker Image

```bash
docker build -t devops-task3:v1 -f Docker/Dockerfile .


The assignment specifically requires Dockerfile and Docker Compose as part of the project deliverables. :contentReference[oaicite:3]{index=3}

---

# 5. Jenkins Pipeline Explanation

Document what you actually implemented in Task 4.

```markdown
## Jenkins CI Pipeline

Jenkins is used to automate the CI process.

The Jenkins pipeline performs the following operations:

1. Checkout the source code from GitHub.
2. Build the Docker image.
3. Run the Docker container.
4. Verify that the application is running.
5. Display the pipeline result.

The pipeline is defined in the Jenkinsfile.

### Pipeline Flow

GitHub
   ↓
Jenkins
   ↓
Checkout main branch
   ↓
Build Docker Image
   ↓
Run Container
   ↓
Verify Application
   ↓
Build Success / Failure

6. Kubernetes Deployment
## Kubernetes Deployment

The Dockerized application is deployed to Kubernetes using Kind.

### Check Cluster

```bash
kind get clusters
kubectl get nodes          kind load docker-image devops-task3:v1 --name devops
kubectl apply -f kubernetes/service.yaml
kubectl get pods
kubectl get deployment
kubectl get svc

```bash
kubectl scale deployment devops-task5 --replicas=3
kubectl get pods

7. Monitoring Setup

## Monitoring

Prometheus and Grafana are used for monitoring the Kubernetes environment.

### Create Monitoring Namespace

```bash
kubectl create namespace monitoring
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install monitoring prometheus-community/kube-prometheus-stack \
  -n monitoring
  kubectl get pods -n monitoring

kubectl port-forward -n monitoring svc/monitoring-grafana 3000:80
kubectl port-forward -n monitoring svc/monitoring-kube-prometheus-prometheus 9090:9090

# 8. Automation Script

Since you completed Task 7, briefly document it:

```markdown
## Automation Script

The `scripts/deploy.sh` script automates application deployment.

It performs:

1. Pull latest code from GitHub.
2. Build Docker image.
3. Remove existing container if present.
4. Start a new container.
5. Verify application availability.
6. Display deployment success or failure.

Run it using:

```bash
chmod +x scripts/deploy.sh
./scripts/deploy.sh







