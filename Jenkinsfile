pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from SCM
                git 'https://github.com/DonRobertoElProgramador/simpledockertest.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    docker.build('simple-echo-container')
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run the Docker container
                    sh 'docker run --rm simple-echo-container'
                }
            }
        }
    }

    post {
        always {
            script {
                // Clean up dangling images
                sh 'docker image prune -f'
            }
        }
    }
}
