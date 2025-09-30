pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/anyanpee/CI-CD-with-Jenkins-Sonarqube-Php-Ansible-Artifactory.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building PHP application...'
                sh 'composer install --no-dev'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Static Code Analysis') {
            steps {
                echo 'Running SonarQube analysis...'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scans...'
            }
        }

        stage('Deploy to Dev') {
            steps {
                echo 'Deploying to development environment...'
                sh 'ansible-playbook -i inventories/dev setup-ci.yml'
            }
        }

        stage('Integration Tests') {
            steps {
                echo 'Running integration tests...'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed - cleaning up...'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
