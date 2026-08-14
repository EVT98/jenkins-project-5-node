pipeline{
    agent{
        docker {
            image 'node:14'
            args '-u root:root'
       }
    }
    stages{
        stage("dependancies install"){
            steps{
                sh 'npm install'
            }
        }
        stage('package'){
            steps{
                sh 'rm -rf my-app-*.tgz || echo ""'
                sh 'npm pack'
            }
        }

    }
    
}