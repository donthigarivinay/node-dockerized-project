pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/donthigarivinay/node-dockerized-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("node-dockerized-project")
                }
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    dockerImage.inside {
                        sh 'npm install'
                        sh 'npm test'
                    }
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-credentials-id') {
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}
