pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting code from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'podman build --format docker -t my-nginx:v1 .'
            }
        }

        stage('Verify Image') {
            steps {
                sh 'podman images'
            }
        }
    }
}
