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
        stage("SonarQube Analysis") {
            steps {
        withSonarQubeEnv('sonar-server') {
    def scannerHome = tool 'sonar-scanner'
    sh '''
    ${scannerHome}/bin/sonar-scanner \
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
}
