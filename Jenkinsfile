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
        stage("Build Image") {
            steps {
                // Use 'bat' for Windows and run the Docker build command
               bat 'docker buildx build -t my-node-app:1.0 Dockerfile'
            }
        }
        

    }
}
