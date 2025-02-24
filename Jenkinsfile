pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/AkshatPandey-2004/Calculator.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo Building the project...'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Running tests...'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo Deploying application...'
            }
        }
    }
}
