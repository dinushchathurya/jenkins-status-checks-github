pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'echo "Building the project"'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests"'
            }
        }
        stage('Status Check') {
            steps {
                sh '''
                    curl -X POST -H "Authorization: Bearer ${GITHUB_TOKEN}" -H "Content-Type: application/json" https://api.github.com/repos/${GITHUB_REPOSITORY_OWNER}/${GITHUB_REPOSITORY_NAME}/statuses/${GITHUB_SHA} -d '{
                        "state": "${STATUS}",
                        "context": "Jenkins Status Check",
                        "description": "Build ${STATUS}"
                    }'
                '''
            }
        }
    }
}


