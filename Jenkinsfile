//pipeline java 11 project demo
pipeline {
  
    agent { label 'openjdk11' }
   
    stages {
      
      stage('Show versions') {
      steps {
           container('docker') {
          sh 'docker --version'
          sh 'java -version'

           }
      }
    }
      
      stage('mvn clean') {
      steps {
           container('docker') {
           echo "Executing mvn clean:"
           sh 'mvn clean'
     
           }
      }
    }

      stage('mvn compile') {
      steps {
           container('docker') {
           echo "mvn compile"
           sh 'mvn compiler:compile'
     
           }
      }
    }

      stage('mvn test compile') {
      steps {
           container('docker') {
           echo "mvn test compile"
           sh 'mvn compiler:testCompile'
     
           }
      }
    }
 
      stage('mvn package') {
      steps {
           container('docker') {
           echo "mvn package"
           sh 'mvn package'
     
           }
      }
    }

      stage('mvn install') {
      steps {
           container('docker') {
           echo "mvn install"
           sh 'mvn install'
     
           }
      }
    }
    
      stage('mvn validate') {
      steps {
           container('docker') {
           echo "mvn validate"
           sh 'mvn validate'
     
           }
      }
    }

      stage('upload to nexus'){
      steps{
          container('docker'){
          nexusArtifactUploader artifacts: [
            [
              artifactId: 'my-app', 
              classifier: '', 
              file: 'target/my-app-1.0.0.jar', 
              type: 'jar'
            ]
          ], 
              credentialsId: 'f90d938e-b977-4030-9c11-7e966e97c54d',
              groupId: 'com.mycompany.app', 
              nexusUrl: 'ad8dbb83dd51a4a199c770bf76c70c27-2073030886.ap-south-1.elb.amazonaws.com:8081',
              nexusVersion: 'nexus3',
              protocol: 'http',
              repository: 'DemoJava',
              version: '1.0.0'
          
          
          }
        
        }
      }
    }
}
