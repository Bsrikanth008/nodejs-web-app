pipeline {
    agent any

    environment {
        IMAGE_NAME = "Bsrikanth008/nodejs-web-app-1:${BUILD_NUMBER}"
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds') // ID from Jenkins Credentials
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'https://github.com/Bsrikanth008/nodejs-web-app.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                sh "echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin"
            }
        }

        stage('Push Docker Image') {
            steps {
                sh "docker push $IMAGE_NAME"
            }
        }

        stage('Deploy Container') {
            steps {
                sh "docker run -d -p 3000:3000 --name node_app_$BUILD_NUMBER $IMAGE_NAME"
            }
        }
    }

    post {
        always {
            echo "Build complete. Status: ${currentBuild.currentResult}"
        }
    }
}
