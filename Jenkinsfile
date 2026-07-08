pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ci-cd-pipeline-jenkins .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop ci-cd-container || true'
                sh 'docker rm ci-cd-container || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 80:80 --name ci-cd-container ci-cd-pipeline-jenkins'
            }
        }
    }
}
