pipeline {
    agent any

    tools {
        nodejs 'yarn'
    }

    stages {
        stage('checkout') {
            steps {
                checkout scm
                sh 'yarn install'
                sh 'yarn build'
            }
        }

        stage('Unit tests') {
            steps {
                sh 'yarn test'
            }
        }

        stage('Integration tests') {
            steps {
                sh 'yarn test:e2e'
            }
        }

        post {
            always {
                junit '**/reports/**/*.xml'
            }
        }
    }
}