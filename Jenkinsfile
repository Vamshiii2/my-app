pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "vamshi0007gangamma/my-app"  // Replace with your Docker Hub username
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Vamshiii2/my-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(DOCKER_IMAGE)
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'vamshi0007gangamma') {
                        docker.image(DOCKER_IMAGE).push('latest')
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage - To be implemented'
            }
        }
    }

    post {
        success {
            echo 'Build succeeded'
        }
        failure {
            echo 'Build failed'
        }
    }
}
