
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
                withSonarQubeEnv('SonarQube') {
                    sh '''
                        sonar-scanner \
                          -Dsonar.projectKey=aws \
                          -Dsonar.projectName=AWS \
                          -Dsonar.sources=.
                    '''
                }
            }
        }
    }
}

