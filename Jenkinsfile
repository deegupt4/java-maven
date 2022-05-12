//pipeline
pipeline {
  
    agent { label 'openjdk11' }
   

    stages {
      
      stage('build docker') {
      steps {
           container('docker') {
          sh 'docker --version'
          sh 'java -version'
     
           }
        
      }
    }
    }
}
