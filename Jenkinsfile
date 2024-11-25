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
                sh ''' mvn sonar:sonar Dsonar.url-http://13.233.56.185:9000/ -Dsonar.login-squ_76ee09c78d860d720d73a685e54da7986e88678e
                        -Dsonar.projectName=Devopss \
                        -Dsonar.java.binaries=. \
                        -Dsonar.projectKey=Devopss '''
                       
                }
            }
        }
    }
