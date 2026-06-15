pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting code from GitHub'
            }
        }

        stage('Build Image') {
            steps {
                sh '''
                whoami
                pwd
                podman build --format docker -t my-nginx:v1 .
                '''
            }
        }

        stage('Verify Image') {
            steps {
                sh 'podman images'
            }
        }
    }
}
