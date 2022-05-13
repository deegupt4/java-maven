//pipeline java 11 project demo
pipeline {
  
    agent { label 'openjdk11' }
   
    stages {
      
      stage('Show versions') {
      steps {
           container('jdk11') {
          sh 'docker --version'
          sh 'java -version'

           }
      }
    }
      
      stage('mvn Cleaning') {
      steps {
           container('jdk11') {
           echo "Executing mvn clean:"
           sh 'mvn clean'
     
           }
      }
    }

      stage('Compiling') {
      steps {
           container('jdk11') {
           echo "mvn compile"
           sh 'mvn compiler:compile'
     
           }
      }
    }

      stage('Testing Compilation') {
      steps {
           container('jdk11') {
           echo "mvn test compile"
           sh 'mvn compiler:testCompile'
     
           }
      }
    }
 
      stage('Packaging') {
      steps {
           container('jdk11') {
           echo "mvn package"
           sh 'mvn package'
     
           }
      }
    }

      stage('Installing') {
      steps {
           container('jdk11') {
           echo "mvn install"
           sh 'mvn install'
     
           }
      }
    }
    
      stage('Testing') {
      steps {
           container('jdk11') {
           echo "mvn validate"
           sh 'mvn validate'
     
           }
      }
    }

      stage('uploading artifact to nexus3'){
      steps{
          container('jdk11'){
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
