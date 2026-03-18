pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "sayeesh1/dock"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/Sayeesh1/dock.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}:latest")
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds', 
                    usernameVariable: 'DOCKER_USER', 
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    // Login to Docker Hub securely
                    sh 'echo $DOCKER_PASS | docker login -u $DOCKER_USER --password-stdin'
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Push the built image to Docker Hub
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-creds') {
                        docker.image("${DOCKER_IMAGE}:latest").push()
                    }
                }
            }
        }

    }

    post {
        success {
            echo '✅ Docker image successfully built and pushed: sayeesh1/dock:latest'
        }
        failure {
            echo '❌ Pipeline failed'
        }
    }
}
