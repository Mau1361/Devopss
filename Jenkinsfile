pipeline {
    agent any
    tools {
        maven 'Maven' // The name of the Maven installation in Jenkins
    }
    environment {
        // Define SonarScanner tool to be used
        SCANNER_HOME = tool name: 'sonar-scanner'
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
        stage("SonarQube Analysis") {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh '''
                    ${SCANNER_HOME}/bin/sonar-scanner \
                        -Dsonar.projectName=Devopss \
                        -Dsonar.java.binaries=. \
                        -Dsonar.projectKey=Devopss \
                        -Dsonar.login=$SONAT_TOKEN
                    '''
                }
            }
        }
    }
}
