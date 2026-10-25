
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Docker image'
                bat 'docker build -t jenkins-web-app .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying web application using Docker'

                bat 'docker rm -f jenkins-web-app-container 2>NUL || exit /b 0'

                bat 'docker run -d --name jenkins-web-app-container -p 8081:80 jenkins-web-app'
            }
        }
    }
}

