1. Objective

The objective of Task 5 is to deploy the Dockerized application to Kubernetes.

The task requires creating Kubernetes resources and deploying the application.

The required resources are:

Namespace
Deployment
Service
ConfigMap
Secret

Ingress and Persistent Volume are optional.

The deployment must be scaled to 3 replicas and tested to verify that the application remains available if one Pod is stopped.

2. What is Kubernetes?

Kubernetes is a container orchestration platform used to deploy, manage and scale containerized applications.

It allows applications running inside containers to be managed automatically.

Kubernetes can manage:

Pods
Deployments
Services
ConfigMaps
Secrets
3. Kubernetes Deployment Architecture

The deployment follows this structure:

Docker Image
↓
Kubernetes Cluster
↓
Namespace
↓
Deployment
↓
Pods
↓
Service
↓
Application

4. Namespace

A Namespace provides logical separation for Kubernetes resources.

A separate namespace can be created for the application.

Example:

apiVersion: v1
kind: Namespace
metadata:
name: devops

Using a namespace keeps the application resources organized and separated from other Kubernetes resources.

5. Deployment

A Kubernetes Deployment manages the application Pods.

It defines important information such as:

Application image
Number of replicas
Container port
Pod labels

The project requires the application to run with 3 replicas.

The architecture is:

Deployment
├── Pod 1
├── Pod 2
└── Pod 3

The Deployment controller attempts to maintain the desired number of replicas.

6. Service

A Kubernetes Service provides network access to the application Pods.

Pods can be replaced or recreated, so their individual identities can change.

The Service provides a stable way to access the application and forwards traffic to the appropriate Pods.

The basic structure is:

Service
↓
Selector
↓
Pod 1
Pod 2
Pod 3

7. ConfigMap

A ConfigMap stores non-sensitive application configuration separately from the container image.

Example:

apiVersion: v1
kind: ConfigMap
metadata:
name: app-config
data:
APP_ENV: "development"

ConfigMaps can be used to provide configuration values to Pods.

8. Secret

A Kubernetes Secret is used to store sensitive information.

Examples include:

Passwords
Tokens
Credentials
API keys

Example:

apiVersion: v1
kind: Secret
metadata:
name: app-secret
type: Opaque

Real credentials should not be committed to a public GitHub repository.

9. Ingress

Ingress is optional for this project.

Ingress can be used to manage HTTP and HTTPS access to applications running inside Kubernetes.

It is not required for the basic deployment described in this task.

10. Persistent Volume

Persistent Volume is also optional for this project.

Persistent storage is generally used when application data needs to remain available even after a Pod is recreated.

For a simple static Nginx application, persistent storage is not required for the basic deployment.

11. Scaling to Three Replicas

The application must be scaled to 3 replicas.

The desired state is:

Deployment
├── Pod 1 - Running
├── Pod 2 - Running
└── Pod 3 - Running

Running multiple replicas provides redundancy.

If one Pod stops, Kubernetes attempts to create a replacement Pod.

For example:

Before:

Pod 1 - Running
Pod 2 - Running
Pod 3 - Running

After Pod 2 stops:

Pod 1 - Running
Pod 2 - Stopped
Pod 3 - Running
Pod 4 - Replacement

The Deployment attempts to maintain three running replicas.

## COMMAND USED
kind get clusters

kubectl get nodes

kubectl apply -f kubernetes/namespace.yaml

kubectl apply -f kubernetes/configmap.yaml

kubectl apply -f kubernetes/secret.yaml

kubectl apply -f kubernetes/deployment.yaml

kubectl apply -f kubernetes/service.yaml

kubectl get pods

kubectl get deployment

kubectl get svc

kubectl get all

kubectl scale deployment <deployment-name> --replicas=3

kubectl get pods

kubectl delete pod <pod-name>

kubectl get pods

kubectl get svc