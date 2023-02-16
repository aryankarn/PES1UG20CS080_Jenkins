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
                // Add deployment steps here
                echo 'Deploying....'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed'
        }
        
        failure {
            echo 'Pipeline failed'
        }
    }
}
