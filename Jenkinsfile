pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/vijay254452/supervehicles.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build & Run') {
            steps {
                sh '''
                  # Build Docker image
                  docker build -t supervehicles .

                  # Stop and remove old container if exists
                  docker rm -f supervehicles_container || true

                  # Run new container with fixed name and port 7584
                  docker run -d -p 7584:8080 --name supervehicles_container supervehicles
                '''
            }
        }
    }
}

