pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out the code...'
                checkout scm
            }
        }
        
        stage('Setup Node.js') {
            steps {
                echo 'Setting up Node.js...'
                bat 'node --version'
                bat 'npm --version'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                echo 'Installing dependencies...'
                bat 'npm install'
            }
        }
        
        stage('Start Application') {
            steps {
                echo 'Starting the application...'
                bat 'npm start &'
                sleep(time: 5, unit: 'SECONDS')
            }
        }
        
        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                bat 'npm test'
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}