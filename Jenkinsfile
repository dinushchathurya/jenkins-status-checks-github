pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    githubNotify context: 'Build', status: 'PENDING'
                }
                // Build step
                sh 'make build'
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
                // Test step
                sh 'make test'
                script {
                    githubNotify context: 'Test', status: 'SUCCESS'
                }
            }
        }
    }

    post {
        failure {
            script {
                githubNotify context: 'Build', status: 'FAILURE'
            }
        }
    }
}
