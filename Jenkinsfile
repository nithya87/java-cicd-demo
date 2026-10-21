pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Source code is fetched from GitHub by Jenkins.'
            }
        }

        stage('Build with Maven') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t java-cicd-demo:latest .'
            }
        }
    }
}