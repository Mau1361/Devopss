pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    environment {
        SONAR_HOST_URL = 'http://13.233.56.185:9000'
        SONAR_TOKEN = 'squ_76ee09c78d860d720d73a685e54da7986e88678e'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh '''
                    mvn sonar:sonar \
                        -Dsonar.host.url=${SONAR_HOST_URL} \
                        -Dsonar.login=${SONAR_TOKEN}
                    '''
                }
            }
        }
    }
}
