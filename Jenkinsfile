pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    // Notify GitHub that the build is pending
                    githubNotify context: 'Build', status: 'PENDING'
                }
                // Build step
                sh 'make build'
                script {
                    // Notify GitHub that the build was successful
                    githubNotify context: 'Build', status: 'SUCCESS'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Notify GitHub that the tests are pending
                    githubNotify context: 'Test', status: 'PENDING'
                }
                // Test step
                sh 'make test'
                script {
                    // Notify GitHub that the tests were successful
                    githubNotify context: 'Test', status: 'SUCCESS'
                }
            }
        }
    }

    post {
        failure {
            script {
                // Notify GitHub of failure
                githubNotify context: 'Build', status: 'FAILURE'
            }
        }
    }
}
