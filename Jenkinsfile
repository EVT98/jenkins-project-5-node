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

        stage('upload artifact') {
            steps {
                sh 'curl -uadmin:APf9HA8iGMfnNpDqqWwUJhoFG1 -T "/var/lib/jenkins/workspace/node-app/my-app-1.2.0.tgz" "http://ec2-54-163-197-213.compute-1.amazonaws.com:8081/artifactory/node-app/node-app:${BU£ILD_NUMBER}"'
            }
        }
    }
}