pipeline {
    agent any
    tools {
        maven 'Maven' // The name of the Maven installation in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Verify Checkout') {
            steps {
                sh 'ls -l'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package -X'
            }
        }
    }
}
