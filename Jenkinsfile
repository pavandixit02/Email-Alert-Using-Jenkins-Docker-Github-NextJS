pipeline {
    agent any

    environment {
        CONTAINER_NAME = "nestjs-app"
        IMAGE_NAME = "nesths-image"
        EMAIL = "pavandixit775@gmail.com"
        PORT = "3300"
    }

    stages {
        stage('Clone Repo'){
            steps{
                git branch: 'main', url: 'https://github.com/pavandixit02/Email-Alert-Using-Jenkins-Docker-Github-NextJS.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }
        stage('Stop & Remove Previous Container') {
            steps {
                sh '''
                    docker stop $CONTAINER_NAME || true
                    docker rm $CONTAINER_NAME || true
                '''
            }
        }
        stage('Docker Container Run') {
            steps {
                sh '''
                    docker run -d -p ${PORT}:${PORT} --name $CONTAINER_NAME $IMAGE_NAME
                '''
            }
        }
        stage('Send Email Notification') {
            steps {
               emailext(
                subject: "NestJS App Deployed Successfully!",
                body: "Your Nest JS app is Deployed! http://localhost:${PORT}/",
                to: "${EMAIL}"
               )
            }
        }

    }
}