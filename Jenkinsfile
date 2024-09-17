pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Send 'pending' status to GitHub
                    githubNotify context: 'Build', status: 'PENDING'
                }
                // Build step
                sh 'make build'  // Replace with your build command
                script {
                    // Send success status to GitHub
                    githubNotify context: 'Build', status: 'SUCCESS'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Send 'pending' status to GitHub
                    githubNotify context: 'Test', status: 'PENDING'
                }
                // Test step
                sh 'make test'  // Replace with your test command
                script {
                    // Send success status to GitHub
                    githubNotify context: 'Test', status: 'SUCCESS'
                }
            }
        }
    }

    post {
        failure {
            script {
                // Notify GitHub of failure in any stage
                githubNotify context: 'Build', status: 'FAILURE'
            }
        }
    }
}
