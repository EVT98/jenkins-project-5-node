pipeline {
   
   agent { docker { image 'node:22-alpine' } }

   environment {
    HOME = "${WORKSPACE}"
    }

   stages {

    stage('Dependecies install') {

        steps {
            sh 'npm install'
        }

    }

   }
}