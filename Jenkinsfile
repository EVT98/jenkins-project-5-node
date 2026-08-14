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

        stage('dependencies install') {
            steps {
                sh 'npm ci'
            }
        }

        stage('start app') {
            steps {
                sh 'npm start &'
                sh 'sleep 5'
            }
        }

        stage('test') {
            steps {
                sh 'npm test -- --timeout 30000'
            }
        }

        stage('package') {
            steps {
                sh 'npm pack'
            }
        }
    }
}