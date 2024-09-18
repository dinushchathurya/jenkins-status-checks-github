pipeline {
    agent any

    environment {
        // Define environment variables
        GITHUB_REPO = 'dinushchathurya/jenkins-status-checks-github'
        GITHUB_CREDENTIALS_ID = 'github-app-secret'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/dinushchathurya/jenkins-status-checks-github.git']]
                ])
            }
        }

        stage('Build') {
            steps {
                // Add your build steps here
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                // Add your test steps here
                echo 'Testing...'
            }
        }
    }

    post {
        success {
            // Notify GitHub on success
            githubNotify(
                context: 'continuous-integration/jenkins',
                status: 'SUCCESS',
                repo: "${env.GITHUB_REPO}",
                credentialsId: "${env.GITHUB_CREDENTIALS_ID}",
                sha: sh(script: 'git rev-parse HEAD', returnStdout: true).trim()
            )
        }

        failure {
            // Notify GitHub on failure
            githubNotify(
                context: 'continuous-integration/jenkins',
                status: 'FAILURE',
                repo: "${env.GITHUB_REPO}",
                credentialsId: "${env.GITHUB_CREDENTIALS_ID}",
                sha: sh(script: 'git rev-parse HEAD', returnStdout: true).trim()
            )
        }
    }
}
