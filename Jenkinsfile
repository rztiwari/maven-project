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
          sh 'mvn clean package'
       }
      post {
        success {
          echo "Now archieving...."
          archieveArtifacts artifacts: '**/target/*.war'
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
