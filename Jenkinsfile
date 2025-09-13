pipeline {
    agent any
    tools {
        maven 'Maven3'
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/vijay254452/supervehicles.git'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Docker Build & Run') {
            steps {
                sh 'docker build -t supervehicles .'
                sh 'docker run -d -p 7584:8080 supervehicles'
            }
        }
    }
}

