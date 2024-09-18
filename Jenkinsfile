pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository code
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Insert build steps here (e.g., npm build, mvn build, etc.)
                // sh 'mvn clean install'  (for Maven projects)
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
                // Insert your testing command here (e.g., npm test, mvn test, etc.)
                // sh 'mvn test' (for Maven projects)
            }
        }
        
        stage('Code Quality') {
            steps {
                echo 'Checking code quality...'
                // Insert linting or code analysis commands here
                // sh 'npm run lint' (for Node.js projects)
            }
        }
    }
    
    post {
        success {
            // Notifies GitHub on successful build
            githubNotify context: 'Jenkins CI', status: 'SUCCESS', description: 'Build and tests passed.'
        }
        failure {
            // Notifies GitHub on failure
            githubNotify context: 'Jenkins CI', status: 'FAILURE', description: 'Build or tests failed.'
        }
    }
}
