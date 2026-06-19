pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting code from GitHub...'
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                sh '''
                echo "Building Docker image..."
                docker build -t my-nginx:v1 .
                '''
            }
        }

        stage('Verify Image') {
            steps {
                sh '''
                echo "Listing Docker images..."
                docker images
                '''
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                set -e

                echo "Stopping old container if exists..."
                docker rm -f web || true

                echo "Running new container..."
                docker run -d -p 8080:80 --name web my-nginx:v1

                echo "Deployment completed successfully"
                '''
            }
        }
    }
}
