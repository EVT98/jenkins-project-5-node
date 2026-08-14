pipeline {
   
   agent { docker { image 'node:22-alpine'  } } // or agent { docker { image 'node:22-alpine' args '-u root:root' } } but I have to delete the env variable

   environment {
    HOME = "${WORKSPACE}"
    }

   stages {

    stage('Dependecies install') {

        steps {
            sh 'npm ci'
        }

    }

    stage('Test') {
        
        steps {
            sh 'npm test'
        }

    }

    stage('Package') {
        
        steps {
            sh 'npm pack'
        }

    }

   }
}