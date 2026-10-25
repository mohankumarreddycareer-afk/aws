
pipeline {
    agent any

    tools {
        sonarQubeScanner 'SonarScanner'
    }

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
                        sonar-scanner \
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
