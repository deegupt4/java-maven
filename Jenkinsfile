//pipeline java 11
pipeline {
  
    agent { label 'openjdk11' }
   

    stages {
      
      stage('build docker') {
      steps {
           container('docker') {
          sh 'docker --version'
          sh 'java -version'
          echo "Build maven jar"
          sh 'mvn -B -DskipTests clean package' 
     
           }
        
      }
    }
    }
}
