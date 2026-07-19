pipeline {
    agent any

    tools {
        SonarQubeScanner 'SonarQube'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Verification') {
            steps {
                sh '''
                    pwd
                    ls -la
                '''
            }
        }

        stage('SonarQube Analysis') {
            steps {
                withSonarQubeEnv('SonarQube') {
                    sh '''
                    sonar-scanner \
		    -Dsonar.projectKey=ShopWave \
                    -Dsonar.projectName=ShopWave \
                    -Dsonar.sources=.
                    '''
                }
            }
        }

    }
}
