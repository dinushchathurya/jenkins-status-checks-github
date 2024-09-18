pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Your build steps here
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                // Your test steps here
            }
        }
    }
    post {
        success {
            echo 'PR passed!'
        }
        failure {
            echo 'PR failed!'
        }
    }
}
