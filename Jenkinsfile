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
                bat 'docker build -t sayeesh1/myimage .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                bat 'docker push sayeesh1/myimage'
            }
        }
    }
}
