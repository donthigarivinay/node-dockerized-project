pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Code for checking out repository
                git 'https://github.com/donthigarivinay/node-dockerized-project.git'
            }
        }
        
        stage('Build') {
            steps {
                // Code for building the project
                sh 'echo "Building project..."'
            }
        }
        
        stage('Test') {
            steps {
                // Code for running tests
                sh 'echo "Running tests..."'
            }
        }
        
        stage('Deploy') {
            steps {
                // Code for deploying the project
                sh 'echo "Deploying project..."'
            }
        }
    }
}
