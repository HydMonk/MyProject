pipeline {
 agent any
 tools {
  maven 'Maven'
 }
 stages {
  stage ('Initialize') {

   steps {
    sh '''
	echo "PATH = $(PATH)"
	echo "M2_HOME = $(M2_HOME)"
     '''
    }
   }

  stage ('Build') {
   steps {
   sh 'mvn clean package'
   }
   }


   stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tiger']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war one@192.168.112.129:/opt/tomcat/webapps/webapp.war'
              }      
           }       
    }

  }

 }
