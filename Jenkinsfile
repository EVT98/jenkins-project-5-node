pipeline {
    
    agent { 
        docker { 
            image 'node:18' 
            args '-u root:root' 
        } 
    }

   stages {

    stage('Dependecies install') {

        steps {
            sh 'npm install'
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