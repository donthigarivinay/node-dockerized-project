pipeline {
    agent any 
    stages{
        stage("checkout"){
            steps{
                 checkout scm
            }
        }
        stage("Test") {
            steps {
                // Install Node.js (if not already installed) using Chocolatey package manager
                bat '''
                choco install nodejs -y
                npm install
                '''

                // Run npm tests
                bat 'npm test'
            }
        }
        stage("Build") {
            steps {
                // Use 'bat' for running commands in Windows
                bat 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Deploy your Docker image
                    echo 'Deploying application...'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-node-app:1.0 .'
            }
        }

    }
}
