
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code fetched from GitHub'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t nithyasri87/java-cicd-demo:latest .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                bat 'docker push nithyasri87/java-cicd-demo:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f k8s\\deployment.yaml'
                bat 'kubectl rollout restart deployment/java-cicd-demo'
                bat 'kubectl rollout status deployment/java-cicd-demo --timeout=120s'
            }
        }
    }
}
