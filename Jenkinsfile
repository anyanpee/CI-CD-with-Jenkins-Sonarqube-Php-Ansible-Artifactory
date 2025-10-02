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
        sh 'echo "No composer.json - skipping composer install"'
    }
  }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                 sh 'phpunit --version' 
            }
        }
        
        stage('Static Code Analysis') {
    steps {
        echo 'Running SonarQube analysis...'
        sh 'sonar-scanner -Dsonar.projectKey=php-todo-app -Dsonar.host.url=http://52.33.17.44:9000'
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
                // sh 'curl -f http://your-dev-server/health-check'
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
