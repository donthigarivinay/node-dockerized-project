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
        stage('Docker Push') {
    steps {
       @echo off
REM DockerHub credentials
set DOCKERHUB_USERNAME=vinayyadav115
set DOCKERHUB_PASSWORD=YourDockerHubPasswordHere

REM Login to DockerHub
docker login -u %DOCKERHUB_USERNAME% -p %DOCKERHUB_PASSWORD%

REM Tag the Docker image
docker tag my-node-app:1.0 %DOCKERHUB_USERNAME%/nodejs-docker

REM Push the Docker image to DockerHub
docker push %DOCKERHUB_USERNAME%/nodejs-docker

REM Logout from DockerHub
docker logout

        }
    }
}

    }
}
