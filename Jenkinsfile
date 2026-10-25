
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/mohankumarreddycareer-afk/aws.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('Sonarqube') {
                    sh '''
                        set -e
                        /opt/sonar-scanner-8.1.0.6389-linux-x64/bin/sonar-scanner \
                          -Dsonar.projectKey=aws \
                          -Dsonar.projectName=AWS \
                          -Dsonar.sources=. \
                          -Dsonar.exclusions=.git/**
                    '''
                }
            }
        }
    }
}
