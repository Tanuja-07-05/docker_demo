pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git 'https://github.com/Tanuja-07-05/docker_demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t tanuja77/myapp:v2 .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push tanuja77/myapp:v2'
            }
        }
    }
}
