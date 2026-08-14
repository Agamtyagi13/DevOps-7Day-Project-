1. Objective

The objective of Task 4 is to create an automated Jenkins CI pipeline for the Dockerized application.

The pipeline connects the GitHub repository with Jenkins and automates the process of obtaining the source code, building the Docker image, running the Docker container, verifying the deployment, and displaying the final build status.

The pipeline should execute successfully without manual intervention.

2. What is Jenkins?

Jenkins is an automation server used to automate software development and deployment processes.

It can automatically perform tasks such as:

Downloading source code
Building applications
Running tests
Building Docker images
Deploying applications
Verifying deployments

In this project, Jenkins is used to automate the Docker build and deployment process.

3. What is CI?

Continuous Integration (CI) is a software development practice where developers frequently integrate their code into a shared repository.

Jenkins can automatically process the new code after it is pushed to GitHub.

The basic workflow is:

GitHub
↓
Jenkins
↓
Checkout Code
↓
Build Docker Image
↓
Run Docker Container
↓
Verify Application
↓
Build Status

4. Jenkins Pipeline Requirements

The Jenkins pipeline performs the following operations:

Pull code from GitHub.
Build the Docker image.
Run the Docker container.
Verify the deployment.
Display the build status.

The pipeline is designed to execute automatically without requiring manual intervention.

5. Jenkinsfile

The pipeline configuration is stored in a file named:

Jenkinsfile

The Jenkinsfile contains different stages that define the CI process.

The main stages are:

Checkout
Build Docker Image
Run Container
Verify Deployment
6. Checkout Stage

In the Checkout stage, Jenkins obtains the project source code from the GitHub repository.

The repository contains the application source code, Docker configuration, Kubernetes configuration and Jenkinsfile.

Jenkins checks out the required project branch and prepares the files for the next pipeline stages.

7. Build Docker Image

After obtaining the source code, Jenkins builds the Docker image using the Dockerfile.

The Dockerfile contains the instructions required to create the application image.

The process is:

Dockerfile
↓
Docker Build
↓
Docker Image

The image can then be used to create a running container.

8. Run Docker Container

After successfully building the Docker image, Jenkins starts a Docker container using the newly created image.

The container runs the Nginx-based web application.

A separate host port can be used for the application to avoid conflicts with Jenkins.

9. Verify Deployment

After starting the container, Jenkins verifies that the application has been deployed successfully.

The verification can check:

Whether the container is running.
Whether the application port is available.
Whether the application responds to a request.

This ensures that the Docker image was not only built successfully but also started correctly.

10. Build Status

At the end of the pipeline, Jenkins displays the result of the build.

The pipeline can have two main results:

SUCCESS

or

FAILURE

If all stages complete successfully, Jenkins marks the build as successful.

If any stage fails, the pipeline is marked as failed.

## Command used

cd ~/DevOps-7Day-Project

git status

git branch

git log --oneline

docker build -t devops-task3:v1 -f Docker/Dockerfile .

docker ps
