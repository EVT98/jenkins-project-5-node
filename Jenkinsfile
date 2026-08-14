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
        stage("dependancies install") {
            steps {
                sh 'npm ci'
            }
        }

        stage("package") {
            steps {
                sh 'rm -f my-app-*.tgz'
                sh 'npm pack'
            }
        }
    }
}