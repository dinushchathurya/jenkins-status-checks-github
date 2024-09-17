pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Send 'pending' status
                    githubNotify context: 'Build', status: 'PENDING'
                }
                // Your build step here
                script {
                    githubNotify context: 'Build', status: 'SUCCESS'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    githubNotify context: 'Test', status: 'PENDING'
                }
                // Your test step here
                script {
                    githubNotify context: 'Test', status: 'SUCCESS'
                }
            }
        }
    }
}


