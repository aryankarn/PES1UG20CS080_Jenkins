pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'g++ -o pes1ug20cs080-1 PES1UG20CS080.cpp'
            }
        }
        stage('Test') {
            steps {
                sh './pes1ug20cs080-1'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Create a Dockerfile to build a Docker image
                    sh 'echo "FROM alpine:latest" > Dockerfile'
                    sh 'echo "COPY pes1ug20cs080-1 /usr/local/bin/" >> Dockerfile'
                    sh 'docker build -t pes1ug20cs080task5 .'
                    // Run the Docker container
                    sh 'docker run -d --name pes1ug20cs080container pes1ug20cs080task5'
                }
            }
        }
    }
    post {
        failure {
            echo 'pipeline failed'
        }
    }
}
