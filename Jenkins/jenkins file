pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'feature/devops',
                    url: 'https://github.com/Agamtyagi13/DevOps-7Day-Project-.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-task3:v1 -f Docker/Dockerfile .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f devops-task4 2>/dev/null || true'
                sh 'docker run -d --name devops-task4 -p 8082:80 --restart unless-stopped devops-task3:v1'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'docker ps'
                sh 'curl -f http://localhost:8082'
            }
        }
    }

    post {
        success {
            echo 'Jenkins pipeline completed successfully.'
        }

        failure {
            echo 'Jenkins pipeline failed.'
        }
    }
}