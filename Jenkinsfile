pipeline {
   
   agent { docker { image 'node:22-alpine'}}

   stages {

    stage('Dependecies install') {

        steps {
            sh 'npm install'
        }

    }

   }
}