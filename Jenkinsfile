pipeline {
    agent {
        label 'master'
    }
    
    stages {
        stage('Checkout') {
            steps {
                echo "Checking out code..."
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo "Building PHP application..."
                sh 'echo "Build completed successfully"'
            }
        }
        
        stage('Test') {
            steps {
                echo "Running tests..."
            }
        }
    }
    
    post {
        always {
            echo "Pipeline completed!"
        }
    }
}
