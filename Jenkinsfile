pipeline {

    agent {
        docker {
            image 'node-chromium:22'
        }
    }


    environment {
        HOME = "${WORKSPACE}"
        PUPPETEER_EXECUTABLE_PATH = '/usr/bin/chromium'
    }

    stages {

        stage('Dependencies install') {

            steps {
                sh 'npm ci'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test -- --timeout 30000'
            }
        }

        stage('Package') {
            steps {
                sh 'npm pack'
            }
        }
    }
}