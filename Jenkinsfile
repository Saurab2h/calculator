pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "saurab2h/calculator"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Saurab2h/calculator.git'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE}")
                }
            }
        }

        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('', 'DockerHubCred') {
                        docker.image("${DOCKER_IMAGE}").push("latest")
                    }
                }
            }
        }
    }
}
