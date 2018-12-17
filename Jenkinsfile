pipeline {
  agent any
  stages {
    stage('Init'){
       steps {
          echo "Testing...."
       }
    }
    
    stage('Build'){
       steps {
          bat 'mvn clean package'
       }
      post {
        success {
          echo "Now archieving...."
          archiveArtifacts artifacts: '**/target/*.war'
        }
      }
    }
    
    stage('Deploy to Staging'){
       steps {
          echo "Code deploying...."
          build job: 'deploy-to-staging'
       }
    }
    
    stage('Deploy to Production'){
       steps {
         echo "Code deploying to prod...."
         timeout(time: 5, unit:'DAYS') {
           input message: 'Approve PRODUCTION deployment?'
         }
         build job: 'deploy-to-prod'
       }
      
      post {
        success{
           echo 'Code deployed to production'
        }
        
        failure{
          echo 'Deployment failed'
        }
      }
    }
  }
}
