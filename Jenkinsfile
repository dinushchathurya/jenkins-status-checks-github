pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository code
                checkout scm
            }
        }
        
        stage('Check for helloworld.txt') {
            steps {
                script {
                    // Check if the helloworld.txt file exists
                    if (fileExists('helloworld.txt')) {
                        echo 'helloworld.txt exists!'
                    } else {
                        error 'helloworld.txt not found!'
                    }
                }
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
            githubNotify context: 'GitHub Status Checker', status: 'SUCCESS', description: 'Build and tests passed.'
        }
        failure {
            // Notifies GitHub on failure
            githubNotify context: 'GitHub Status Checker', status: 'FAILURE', description: 'Build or tests failed.'
        }
    }
}
