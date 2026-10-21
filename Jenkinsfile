
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
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    bat 'echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin'
                    bat 'docker push nithyasri87/java-cicd-demo:latest'
                    bat 'docker logout'
                }
            }
        }
    }
}
