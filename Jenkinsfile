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
                script {
                    def scannerHome = tool 'SonarScanner'

                    withSonarQubeEnv('Sonarqube') {
                        sh """
                            "\${scannerHome}/bin/sonar-scanner" \
                              -Dsonar.projectKey=aws \
                              -Dsonar.projectName=AWS \
                              -Dsonar.sources=. \
                              -Dsonar.exclusions=.git/**
                        """
                    }
                }
            }
        }
    }
}
