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
    sh 'JENKINS_NODE_COOKIE=dontKillMe nohup java -jar -Dserver.port=8083 target/spring-petclinic-2.1.0.BUILD-SNAPSHOT.jar &'
    }
    }

     
    
       
        
 }
}


