pipeline {
    agent {
        docker {
            image 'node:16-buster-slim'
            args '-p 3000:3000'
        }
    }

    stages {
        stage('Clean') {
            steps {
                sh 'rm -rf node_modules package-lock.json'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install --legacy-peer-deps'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
    }
}