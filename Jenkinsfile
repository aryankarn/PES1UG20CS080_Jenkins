pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                sh 'g++ -o YOUR_SRN-1 your_cpp_file.cpp'
            }
        }
        
        stage('Test') {
            steps {
                sh './YOUR_SRN-1'
            }
        }
        
        stage('Deploy') {
            steps {
                // Add deployment steps here
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
