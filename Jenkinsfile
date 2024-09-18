pipeline {
    agent any
    triggers {
        githubPush()
    }
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Add test steps here
            }
        }
    }
    post {
        success {
            githubChecks status: 'SUCCESS', name: 'Jenkins Status Checker'
        }
        failure {
            githubChecks status: 'FAILURE', name: 'Jenkins Status Checker'
        }
    }
}