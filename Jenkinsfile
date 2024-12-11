pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Devopspractical-aws/ecommerce-pipeline'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t user-service ./user-service
                '''
            }
        }
        stage('Push to AWS ECR') {
            steps {
                sh '''
                aws ecr get-login-password --region eu-west-2 | docker login --username AWS --password-stdin 376713416462.dkr.ecr.eu-west-2.amazonaws.com
                docker tag user-service 376713416462.dkr.ecr.eu-west-2.amazonaws.com/user-service
                docker push 376713416462.dkr.ecr.eu-west-2.amazonaws.com/user-service
                '''
            }
        }
    }
}
