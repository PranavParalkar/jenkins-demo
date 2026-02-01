pipeline {
    agent any

    environment {
        IMAGE_NAME = "pranavparalkar21/merged-doc"
        IMAGE_TAG  = "4.0.0"
        DOCKER_BUILDKIT = "0"
    }

    stages {

        stage('Start') {
            steps {
                echo "🚀 Pipeline started"
            }
        }

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/PranavParalkar/jenkins-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
                '''
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'pranav',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {
                    sh '''
                    echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                    '''
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh '''
                docker push ${IMAGE_NAME}:${IMAGE_TAG}
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Docker image built & pushed successfully 🚀"
        }
        failure {
            echo "❌ Pipeline failed"
        }
    }
}
