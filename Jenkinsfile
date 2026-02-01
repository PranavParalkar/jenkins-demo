pipeline {
    agent any
    stages {
        stage('Sanity') {
            steps {
                sh 'git status'
                echo 'Repo is checked out correctly 🚀'
            }
        }
    }
}


// pipeline {
//     agent any

//     environment {
//         IMAGE_NAME = "pranavparalkar21/merged-doc" // lowercase is safer
//         IMAGE_TAG = "3.0.0"
//     }

//     stages {

//         stage('Try') {
//             steps {
//                 echo "hello i have started"
//             }
//         }

//         stage('Checkout Code') {
//             steps {
//                 git branch: 'main', url: 'https://github.com/PranavParalkar/jenkins-demo.git'
//             }
//         }

//         stage('Build Docker Image') {
//             steps {
//                 script {
//                     echo "Building Docker image..."
//                     def customImage = docker.build("${IMAGE_NAME}:${IMAGE_TAG}")
//                     env.IMAGE_ID = customImage.id
//                 }
//             }
//         }

//         stage('Push Docker Image') {
//             steps {
//                 script {
//                     docker.withRegistry('https://index.docker.io/v1/', 'pranav') {
//                         docker.image("${IMAGE_NAME}:${IMAGE_TAG}").push()
//                     }
//                 }
//             }
//         }
//     }

//     post {
//         success { echo "Docker image successfully built and pushed 🚀" }
//         failure { echo "Pipeline failed ❌" }
//     }
// }