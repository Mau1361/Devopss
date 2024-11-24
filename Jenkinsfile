pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage('Build maven project') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/development']],
                    extensions: [],
                    userRemoteConfigs: [[url: 'https://github.com/Mau1361/Devopss']]
                ])
                sh 'mvn clean install'
            }
        }
    }
}
