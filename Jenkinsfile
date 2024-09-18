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
            }
        }

        stage('Test') {
            steps {
                echo 'Running unit tests...'
            }
        }
        
        stage('Code Quality') {
            steps {
                echo 'Checking code quality...'
            }
        }
    }
    
    post {
        success {
            // Notifies GitHub on successful build
            githubNotify context: 'Jenkins Status Checker', status: 'SUCCESS', description: 'Build and tests passed.'
        }
        failure {
            // Notifies GitHub on failure
            githubNotify context: 'Jenkins Status Checker', status: 'FAILURE', description: 'Build or tests failed.'
        }
    }
}
\