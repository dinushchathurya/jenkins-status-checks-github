pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the repository
                checkout scm
            }
        }
        
        stage('Check for helloworld.txt') {
            steps {
                script {
                    // Check if the helloworld.txt file exists
                    if (fileExists('helloworld.txt')) {
                        echo 'helloworld.txt exists!'
                    } else {
                        error 'helloworld.txt not found!'
                    }
                }
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
