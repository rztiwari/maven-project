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
    
    stage('Deploy'){
       steps {
          echo "Code deployed...."
       }
    }
  }
}
