pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                // Use ./gradlew to build the project
                sh './gradlew assemble'
            }
        }
        
        stage('Test') {
            steps {
                // Use ./gradlew to run tests
                sh './gradlew test'
            }
        }
    }
    
    post {
        always {
            // Archive the build artifacts (if applicable)
            archiveArtifacts artifacts: '**/build/libs/*.jar', allowEmptyArchive: true
        }
        
        success {
            // Notification or actions to take when the build succeeds
            echo 'Build successful!'
        }
        
        failure {
            // Notification or actions to take when build or tests fail
            echo 'Build or tests failed!'
        }
    }
}

