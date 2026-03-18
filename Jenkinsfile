pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Sayeesh1/dock.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t sayeesh1/image:v1 .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                sh 'docker push sayeesh1/image:v1'
            }
        }
    }
}
