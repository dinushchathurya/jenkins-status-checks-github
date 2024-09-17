pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Simulate a build process
                script {
                    // Send build status as "in progress"
                    githubNotify context: 'Build', status: 'PENDING'
                }
                sh 'sleep 10' // Simulate build delay
                // Send build status as "success"
                githubNotify context: 'Build', status: 'SUCCESS'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests...'
                // Simulate a test process
                script {
                    // Send test status as "in progress"
                    githubNotify context: 'Test', status: 'PENDING'
                }
                sh 'sleep 5' // Simulate test delay
                // Simulate test failure
                script {
                    if (env.BRANCH_NAME == 'test-fail') {
                        githubNotify context: 'Test', status: 'FAILURE'
                        error 'Tests failed!'
                    } else {
                        githubNotify context: 'Test', status: 'SUCCESS'
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            cleanWs()
        }
    }
}