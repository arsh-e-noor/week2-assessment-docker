pipeline {
    agent any

    environment {
        BACKEND_IMAGE = "yourdockerhub/backend"
        FRONTEND_IMAGE = "yourdockerhub/frontend"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/arsh-e-noor/week2-assessment-docker'
            }
        }

        stage('Build Backend Image') {
            steps {
                sh 'docker build -t $BACKEND_IMAGE:v1 ./MERN-E-Commerce-Store/backend'
            }
        }

        stage('Build Frontend Image') {
            steps {
                sh 'docker build -t $FRONTEND_IMAGE:v1 ./MERN-E-Commerce-Store/frontend'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Backend') {
            steps {
                sh 'docker push $BACKEND_IMAGE:v1'
            }
        }

        stage('Push Frontend') {
            steps {
                sh 'docker push $FRONTEND_IMAGE:v1'
            }
        }
    }
}