pipeline {
    agent any 
    stages{
        stage("checkout"){
            steps{
                 checkout scm
            }
        }
        stage("Test"){
            steps{
                sh 'sudo npm install'
                sh 'npm test'
            }
        }
        stage{
            steps{
                sh 'npm run build'
            }
        }
        stage('Build') {
            steps {
                sh 'echo "Building project"'
            }
        }

    }
}
