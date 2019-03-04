pipeline {
  agent any
  tools {
   maven 'maven3.6.0'
   jdk 'java1.8.0'
 }
 stages {
  stage('Build') {
  steps {
    sh "mvn -B -DskipTests clean package"
    }
    }
 

    stage('Test') {
            steps {
                sh 'mvn test'
            }
     }
   
   stage ('Deploy') {
  steps {
    sh "nohup java -jar -Dserver.port=8083 target/spring-petclinic-2.1.0.BUILD-SNAPSHOT.jar &"
    }
    }

     
    
       stage('Upload'){
         steps {
           
            sh 'curl -X PUT -u admin:5r5h7sb5w -T target/my-app-1.0-SNAPSHOT.jar "http://13.71.125.61:8081/artifactory/example-repo-local/spring-petclinic-2.1.0.BUILD-SNAPSHOT.jar"'
         }
       }
        
 }
}


