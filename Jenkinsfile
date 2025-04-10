pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'srikanthberla/first-project'
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
                sh "docker run -d -p 3000:3000 ${DOCKER_IMAGE}"
            }
        }
    }
}
