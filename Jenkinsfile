pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Checkout from the GitHub repository
                checkout scm
            }
        }
        stage('Verify Checkout') {
            steps {
                // List files to ensure checkout worked
                sh 'ls -l'
            }
        }
        stage('Build') {
            steps {
                // Build the project with Maven
                sh 'mvn clean package -X'
            }
        }
    }
}
