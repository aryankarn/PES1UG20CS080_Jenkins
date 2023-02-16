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
                sh 'if [ -f ./pes1ug20cs080-1 ]; then ./pes1ug20cs080-1; else echo "ERROR: pes1ug20cs080-1 not found"; exit 1; fi'
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Create a Dockerfile to build a Docker image
                    sh 'echo "FROM alpine:latest" > ${WORKSPACE}/Dockerfile'
                    sh 'echo "COPY pes1ug20cs080-1 /usr/local/bin/" >> ${WORKSPACE}/Dockerfile'
                    sh 'docker build -t pes1ug20cs080task5 ${WORKSPACE}'
                    // Run the Docker container
                    sh 'docker run -d --name pes1ug20cs080container pes1ug20cs080task5'
        }
    }
}

    post {
        failure {
            echo 'pipeline failed'
        }
    }
}
