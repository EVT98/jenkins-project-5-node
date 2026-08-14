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

        stage("start application") {
            steps {
                sh '''
                    npm start > app.log 2>&1 &
                    echo $! > app.pid
                    sleep 5
                '''
            }
        }

        stage("test") {
            steps {
                sh 'npm test -- --timeout 30000'
            }
        }

        stage("package") {
            steps {
                sh 'rm -f my-app-*.tgz'
                sh 'npm pack'
            }
        }
    }

    post {
        always {
            sh '''
                if [ -f app.pid ]; then
                    kill $(cat app.pid) || true
                fi
            '''
        }
    }
}