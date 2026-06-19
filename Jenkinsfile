pipeline {
 agent any

 environment {
     IMAGE_NAME="my-nginx:v1"
 }

 stages {

 stage('Checkout') {
 steps {
 echo 'Getting code'
 }
 }

 stage('Build Image') {
 steps {
 sh 'docker build -t $IMAGE_NAME .'
 }
 }

 stage('Verify') {
 steps {
 sh 'docker images'
 }
 }

 stage('Deploy') {
 steps {

 sh '''
 docker stop web || true

 docker rm web || true

 docker run -d \
 -p 8080:80 \
 --name web \
 $IMAGE_NAME
 '''
 }

 }

 }

}
