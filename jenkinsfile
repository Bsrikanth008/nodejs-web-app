pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'srikanthberla/first-project'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Bsrikanth008/nodejs-web-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${DOCKER_IMAGE}")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-creds-id') {
                        dockerImage.push()
                    }
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                sh "docker run -d -p 8080:80 ${DOCKER_IMAGE}"
            }
        }
    }
}
