pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Send status as 'in progress'
                    githubNotify context: 'Build', status: 'PENDING'
                }
                // Your build logic here
                script {
                    // Send success status
                    githubNotify context: 'Build', status: 'SUCCESS'
                }
            }
        }
    }
}
