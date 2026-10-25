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
                    def scannerHome = tool(
                        name: 'SonarScanner',
                        type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                    )

                    withSonarQubeEnv('Sonarqube') {
                        sh """
                            set -e
                            echo "Scanner location: ${scannerHome}"
                            ls -l "${scannerHome}/bin/sonar-scanner"
                            "${scannerHome}/bin/sonar-scanner" \
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
