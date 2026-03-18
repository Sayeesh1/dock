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
                bat 'docker build -t myimage .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                bat 'docker push myimage'
            }
        }
    }
}
