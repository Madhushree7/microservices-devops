pipeline {
    agent any

    tools {
        sonarQubeScanner 'SonarScanner'
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
		    -Dsonar.projectKey=shopwave \ 
                    -Dsonar.projectName=ShopWave \
                    -Dsonar.sources=.
                    '''
                }
            }
        }

    }
}
