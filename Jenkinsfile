pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                // Insert your build steps here (e.g., npm install, mvn clean install)
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Insert your test steps here (e.g., npm test, mvn test)
            }
        }

        stage('Code Quality') {
            steps {
                echo 'Running code quality checks...'
                // Insert code analysis or linting steps here (e.g., ESLint, Checkstyle)
            }
        }
    }

    post {
        success {
            // Notify GitHub of success
            githubNotify context: 'Jenkins Status Checker', status: 'SUCCESS', description: 'Build passed!'
        }
        failure {
            // Notify GitHub of failure
            githubNotify context: 'Jenkins Status Checker', status: 'FAILURE', description: 'Build failed!'
        }
    }
}
